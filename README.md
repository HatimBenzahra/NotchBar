# NotchFlow

A macOS menu bar app that displays a customizable clock in the MacBook Pro notch area. The clock sits quietly in the notch, expands on hover, and supports multiple themes and font styles.

## Requirements

- macOS 14.0 or later
- MacBook Pro with notch display
- Xcode 15+ (to build from source)

## Stack

- Swift 5.9, SwiftUI, AppKit
- XcodeGen for project generation
- macOS 14.0+ deployment target

## Features

- Compact animated clock in the notch area (colon blinks on each second)
- Hover-triggered expandable panel with additional info
- 8 accent color themes: Electric Blue, Violet, Coral, Emerald, and more
- 4 font style choices for the clock display
- Canvas-based animated spider widget
- Smart notch detection using screen safe area insets
- Runs as a background accessory app with no dock icon

## Architecture

The app follows MVVM. `NotchViewModel` owns all state and drives the SwiftUI views. A custom `NSPanel` subclass positions the window precisely over the notch. `ThemeManager` handles color and font preferences and persists them to `UserDefaults`.

```
NotchViewModel
    ├── ThemeManager       (colors, fonts, persistence)
    ├── NotchPanel         (custom NSPanel, positioning)
    └── ClockView          (SwiftUI, animated colon)
        └── SpiderWidget   (Canvas-based animation)
```

## Getting Started

```bash
# Generate the Xcode project
xcodegen generate

# Open and build
open NotchBar.xcodeproj
```

Build and run the scheme in Xcode. The app will appear in the notch area immediately on launch.

## Configuration

All preferences are accessible from the expandable panel. Changes apply live without restarting the app.

| Setting      | Options                                      |
|--------------|----------------------------------------------|
| Accent color | Electric Blue, Violet, Coral, Emerald, +4    |
| Font style   | 4 choices (system, monospaced, rounded, serif)|

## License

MIT
