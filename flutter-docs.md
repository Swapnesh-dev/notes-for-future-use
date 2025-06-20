# Most Used Flutter Widgets

| No. | Widget Name               | Similar HTML Tag | Usage | When to Use | When Not to Use |
|----|--------------------------|----------------|--------|-------------|----------------|
| 1  | **Container**           | `<div>`         | Used for layout, decoration, padding, and constraints. | When you need a flexible box with styling. | Avoid excessive nesting, prefer layout widgets. |
| 2  | **Row & Column**        | `<div style="display: flex">` | Arranges widgets horizontally (`Row`) or vertically (`Column`). | For simple layout structuring. | When needing a complex responsive layout; consider `Flex`. |
| 3  | **Stack**               | `<div style="position: absolute">` | Places widgets on top of each other. | For overlapping elements (e.g., floating buttons over images). | When simple column/row layout suffices. |
| 4  | **Expanded & Flexible** | `<div style="flex-grow: 1">` | Adjusts child widgets to fill space. | Inside `Row`, `Column`, or `Flex` for responsive UI. | When child widgets should not expand. |
| 5  | **Align**               | `<div style="text-align: center">` | Aligns child widgets within a parent. | When needing custom positioning. | When `Row` or `Column` suffices. |
| 6  | **Padding**             | `<div style="padding: 10px">` | Adds internal spacing around a widget. | When adding spacing without affecting layout structure. | Use `Margin` for external spacing. |
| 7  | **Scaffold**            | `<body>`        | Basic structure with app bar, body, floating action button, and drawer. | When building a standard Material Design app layout. | For lightweight UI where `Container` or `Column` suffices. |
| 8  | **AppBar**              | `<header>`      | Displays a top bar with title and actions. | When a navigation or title bar is required. | When a custom design without an app bar is needed. |
| 9  | **TextField**           | `<input>`       | Collects user input. | For user text input fields. | When a read-only display is needed, use `Text` instead. |
| 10 | **ElevatedButton**      | `<button>`      | A material-styled button. | For main call-to-actions. | When a less prominent button is needed, consider `OutlinedButton` or `TextButton`. |
| 11 | **ListView**            | `<ul>` or `<div style="overflow-y: scroll">` | Scrollable list of widgets. | When displaying a list of dynamic items. | When a small, static list is needed. |
| 12 | **GridView**            | `<div style="display: grid">` | Displays widgets in a grid. | When displaying structured, tile-like UI. | When a linear list works better. |
| 13 | **SingleChildScrollView** | N/A | Makes a single child widget scrollable. | When content overflows the screen. | For lists; use `ListView` instead. |
| 14 | **FutureBuilder & StreamBuilder** | N/A | Handles asynchronous data. | When fetching data from an API or stream. | When data is static. |
| 15 | **AnimatedContainer** | N/A | Creates smooth animations for property changes. | When transitioning between states. | When animations are unnecessary. |
| 16 | **BottomNavigationBar** | `<nav>` | Displays a bottom navigation bar. | For navigation between major sections. | When a `Drawer` or `TabBar` is more appropriate. |
| 17 | **TabBar & TabBarView** | N/A | Creates tabbed navigation. | When users need to switch between views easily. | When fewer than two tabs exist. |
| 18 | **Drawer** | `<aside>` | Provides side navigation. | For navigation-heavy apps. | When a bottom navigation bar is better suited. |
| 19 | **AlertDialog & SnackBar** | N/A | Displays alerts and feedback messages. | For user notifications. | Overuse can annoy users. |
| 20 | **Hero** | N/A | Creates shared element transitions. | When navigating between screens with common elements. | When animations are unnecessary. |
| 21 | **Divider** | `<hr>` | Creates a horizontal separator. | When separating content visually. | When excessive spacing is preferred. |
| 22 | **Card** | `<div class="card">` | Creates a Material-style card container. | For grouping related content. | When a plain `Container` suffices. |
| 23 | **Chip** | `<span class="badge">` | Displays small pieces of information. | For tags, labels, or filters. | When a button or text suffices. |
| 24 | **Tooltip** | `title` attribute | Shows additional information on hover or long-press. | For adding hints to elements. | When UI is self-explanatory. |
| 25 | **InkWell** | N/A | Adds a ripple effect on tap. | When customizing touchable elements. | When `GestureDetector` suffices. |
| 26 | **GestureDetector** | N/A | Detects gestures like taps, swipes, and long presses. | When needing advanced touch interactions. | When a simple button suffices. |
| 27 | **Draggable & DragTarget** | N/A | Enables drag-and-drop functionality. | When creating drag-and-drop UI. | When interactions should be static. |
| 28 | **ReorderableListView** | N/A | Creates a list where items can be reordered. | When allowing users to reorder items dynamically. | When items should remain fixed. |
| 29 | **Slider** | `<input type="range">` | Selects a value from a range. | For volume, brightness, etc. | When step-based selection is better. |
| 30 | **Switch** | `<input type="checkbox">` | Toggles a boolean value. | For enabling/disabling features. | When a button or dropdown is clearer. |
| 31 | **Checkbox & Radio** | `<input type="checkbox">` `<input type="radio">` | Allows multiple or single selections. | For selecting options. | When a dropdown is better. |
| 32 | **ProgressIndicator** | N/A | Displays loading progress. | When indicating loading states. | When unnecessary for instant actions. |
| 33 | **Wrap** | `<div style="display: flex; flex-wrap: wrap">` | Arranges widgets in a wrapping layout. | When content should wrap within constraints. | When a simple row/column suffices. |
| 34 | **CustomPaint** | N/A | Draws complex custom shapes. | When needing custom graphics. | When standard UI elements suffice. |
| 35 | **SizedBox** | `<div style="width: X; height: Y">` | Defines fixed spacing or dimensions. | When needing empty space or fixed sizing. | When flexible layouts are preferred. |
| 36 | **ClipRRect** | N/A | Clips widgets with rounded corners. | When needing rounded UI elements. | When default border-radius styles suffice. |
| 37 | **Transform** | N/A | Applies transformations like scaling, rotating. | When modifying widget appearance. | When CSS styles suffice. |
| 38 | **Opacity** | N/A | Adjusts widget transparency. | When controlling visibility smoothly. | Use `Visibility` for complete hiding. |
| 39 | **Flexible** | N/A | Resizes widgets flexibly. | When child widgets need proportional spacing. | When fixed sizing is needed. |
| 40 | **Flow** | N/A | Creates highly customized layouts. | When default layouts are insufficient. | When simpler layout options exist. |
| 41 | **Positioned** | N/A | Positions widgets inside `Stack`. | When absolute positioning is required. | When using `Row` or `Column` is sufficient. |
| 42 | **Visibility** | `display: none` | Shows or hides a widget. | When toggling visibility dynamically. | Use `Opacity` if smooth transitions are needed. |
| 43 | **AspectRatio** | N/A | Maintains a specific width-to-height ratio. | When ensuring a fixed aspect ratio for a widget. | When flexible sizing is needed. |
| 44 | **FittedBox** | `object-fit: cover/contain` | Scales child widgets within constraints. | When preventing overflow while maintaining proportions. | When fixed dimensions are required. |
| 45 | **PageView** | N/A | Enables horizontal or vertical swiping between pages. | When implementing swipeable pages. | When `ListView` is more appropriate. |
| 46 | **NestedScrollView** | N/A | Combines `SliverAppBar` and scrollable content. | When needing a collapsing header with scrollable content. | When `ListView` suffices. |
| 47 | **SliverList & SliverGrid** | N/A | Creates optimized scrolling lists and grids. | When handling large scrollable lists efficiently. | When a simple `ListView` or `GridView` suffices. |
| 48 | **RichText** | `<span>` with styles | Displays styled text with multiple styles in one widget. | When mixing different text styles in a single block. | When a single style suffices, use `Text`. |
| 49 | **SelectableText** | `<p contenteditable>` | Allows users to copy and select text. | When needing text selection. | When text should remain static. |
| 50 | **ShaderMask** | N/A | Applies gradient masks to child widgets. | When creating text/image masking effects. | When simple styling suffices. |
| 51 | **BackdropFilter** | `filter: blur()` | Blurs the background behind a widget. | When achieving frosted glass effects. | When blurring is unnecessary. |
| 52 | **ListWheelScrollView** | N/A | Creates a 3D spinning wheel effect. | When designing a picker-like UI. | When `ListView` is more appropriate. |
| 53 | **Hero** | N/A | Animates shared elements between screens. | When transitioning between pages smoothly. | When no visual transition is needed. |
| 54 | **CupertinoWidgets** | N/A | Implements iOS-styled UI components. | When developing an iOS-style app. | When a Material-style UI is required. |
| 55 | **CupertinoPageRoute** | N/A | Provides iOS-style navigation transitions. | When designing an iOS-native experience. | When Material transitions suffice. |
| 56 | **NotificationListener** | N/A | Listens for scroll and other notifications. | When responding to scroll or custom notifications. | When event listeners are unnecessary. |
| 57 | **ValueListenableBuilder** | N/A | Listens to `ValueNotifier` changes and rebuilds UI. | When using `ValueNotifier` for state updates. | When `StatefulWidget` is more appropriate. |
| 58 | **PopupMenuButton** | `<select>` | Displays a dropdown-style popup menu. | When providing multiple selectable actions. | When `DropdownButton` is more suitable. |
| 59 | **RepaintBoundary** | N/A | Optimizes performance by isolating widget repaints. | When reducing excessive repaints in complex UIs. | When unnecessary for simple UIs. |
| 60 | **InteractiveViewer** | N/A | Enables pinch-to-zoom and panning interactions. | When adding zooming functionality to images or widgets. | When interactions are unnecessary. |
