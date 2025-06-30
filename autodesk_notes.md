
# Autodesk Forge & Three.js Camera Sync Notes

## Goal
Synchronize two separate 3D viewers:
1. **Forge Viewer** (Three.js r71)
2. **React-Three-Fiber HDR scene** (modern Three.js)

...using a shared camera pose (position, target, up).

---

## Recommended Sync Strategy

### Use `position`, `target`, and `up` vectors
Avoid working directly with quaternions. Instead:
- `position`: camera location
- `target`: look-at point
- `up`: usually (0, 0, 1) for Forge

### Forge Viewer: use navigation API
```js
viewer.navigation.setView(position, target);
viewer.navigation.setCameraUpVector(new THREE.Vector3(0, 0, 1));
```

To animate between poses:
```js
viewer.navigation.setPosition(...);
viewer.navigation.setTarget(...);
viewer.navigation.setCameraUpVector(...);
```

### React-Three-Fiber
In the `useFrame` loop:
```js
camera.position.copy(cameraPose.current.position);
camera.up.copy(cameraPose.current.up);
camera.lookAt(cameraPose.current.target);
```
Or, derive `target` from quaternion:
```js
const forward = new THREE.Vector3(0,0,-1).applyQuaternion(cameraPose.current.quaternion);
camera.lookAt(camera.position.clone().add(forward));
```

---

## Shared Camera Pose Object
Maintain a shared `cameraPose` object:
```js
cameraPose.current = {
  position: new THREE.Vector3(...),
  target: new THREE.Vector3(...),
  up: new THREE.Vector3(0, 0, 1)
};
```
Update this on user interaction or point change.

---

## Coordinate System Alignment
- Forge uses Z-up
- Ensure both viewers are using the same up-axis
- Units and coordinate origins must match
- Use a known transform if coordinate spaces differ

### Optional: compute look-at quaternion from position/target
```js
const m = new THREE.Matrix4().lookAt(position, target, up);
quaternion.setFromRotationMatrix(m);
```

---

## Summary
- Drive both cameras via shared `{position, target, up}`
- Use Forge's `viewer.navigation.setView()`
- Use R3F's `camera.position` + `lookAt()`
- Ensure coordinate systems are aligned
- Smooth transitions via tweening/interpolation

---

## References
- Forge camera = position + target + up: [Forge Docs](https://aps.autodesk.com/en/docs/viewer/v7/reference/javascript/navigation/)
- Camera sync/tween example: [Autodesk Blog](https://forge.autodesk.com/blog/synchronizing-cameras-multiple-viewers)
- Three.js `lookAt`/quaternion tips: [Three.js Docs](https://threejs.org/docs/index.html#api/en/math/Matrix4.lookAt)
