# Perpetual Task Companion (PTC)

> **Never lose sight of what you committed to today, this week, this quarter, this year — without having to switch context.**

PTC is a lightweight Windows desktop productivity companion that helps you stay on top of your commitments across **four time horizons**: Daily, Weekly, Quarterly, and Yearly. Built with Flutter and Hive for a native, always-available experience.

---

## Features

- **📋 Four-horizon task management** — Daily, Weekly, Quarterly, and Yearly views, all in one app.
- **🧩 Always-on-top pill overlay** — A tiny, glanceable capsule that floats on your screen showing remaining tasks. Hover to expand into a full task panel.
- **⚡ Global hotkeys** — `Win + T` to toggle the overlay, `Ctrl + Shift + T` for instant task capture from any app.
- **🔥 Streak tracking** — Consecutive-day completion streak with best-streak record, displayed in the sidebar and overlay.
- **📊 Dashboard with charts** — Period summary cards, a 7-day completion bar chart (`fl_chart`), and stat cards for current/best streak.
- **🎉 Celebration confetti** — Full-screen confetti burst on every task completion (positive reinforcement).
- **🎯 Quick add** — Spotlight-style dialog with suffix parsing: `"Pay invoice w"` → weekly task.
- **🔄 Reactive state** — Changes in any view reflect instantly everywhere via Riverpod.
- **⚙️ Customizable overlay** — Adjust corner position, opacity, hover delay, and streak visibility from Settings.
- **💾 Persistent local storage** — All data stored locally via Hive; survives restarts.
- **🍱 System tray** — Background persistence with tray menu (Show, Quick Add, Keep on Top, Quit).
- **🌱 Seed data** — 10 demo tasks and 6 days of history on first launch so the dashboard is never empty.

---

## Installation

### Prerequisites

- **Flutter SDK** 3.44+ ([install guide](https://docs.flutter.dev/get-started/install))
- **Windows 10/11** (64-bit)

### Setup

```bash
# Clone the repository
git clone https://github.com/yourusername/ptc.git
cd ptc

# Get dependencies
flutter pub get

# Run the app (debug mode)
flutter run

# Build for release
flutter build windows
```

The release executable will be at `build\windows\x64\runner\Release\ptc.exe`.

---

## Usage

### Main Window

Navigate through the sidebar to manage tasks across four periods:

| View     | Description |
|----------|-------------|
| Dashboard | At-a-glance summary with progress cards, completion chart, and streak stats |
| Daily     | Today's tasks |
| Weekly    | This week's tasks |
| Quarterly | This quarter's tasks |
| Yearly    | This year's tasks |
| Settings  | Overlay customization, hotkey reference, reset demo data |

### Pill Overlay

- The pill sits in a corner of your screen (default: top-right).
- **Collapsed**: Shows task count, status dot, and optional streak chip.
- **Hover** (after delay): Pill becomes interactive.
- **Click**: Expands into a full panel with tabs, task list, and quick-add.

### Quick Add

Press `Ctrl + Shift + T` from anywhere to open the Quick Add dialog. Use suffixes to set the period:

```
"Review PRs w"     → Weekly task
"Hire engineers q" → Quarterly task  
"Read books y"     → Yearly task
"Buy milk d"       → Daily task (default)
```

### Hotkeys

| Action | Shortcut |
|--------|----------|
| Toggle overlay | `Win + T` |
| Quick add | `Ctrl + Shift + T` |
| Cancel/Close | `Esc` |
| Submit form | `Enter` |

---

## Tech Stack

| Layer | Choice |
|---|---|
| Framework | Flutter 3.x (Windows desktop) |
| State | Riverpod |
| Storage | Hive (local, no backend) |
| Charts | fl_chart |
| Windows mgmt | window_manager, tray_manager |
| Hotkeys | hotkey_manager |
| Confetti | confetti package |
| IDs | uuid |

---

## Project Structure

```
lib/
├── main.dart                     # Entry point, window/tray/hotkey setup
├── app.dart                      # MaterialApp with PTC theme
├── models/                       # Data models + Hive TypeAdapters
│   ├── task.dart
│   ├── period.dart
│   ├── daily_history.dart
│   └── settings.dart
├── storage/
│   └── hive_storage.dart         # Hive CRUD, streak, seed data
├── providers/                    # Riverpod state management
│   ├── task_provider.dart
│   ├── settings_provider.dart
│   ├── streak_provider.dart
│   └── celebration_provider.dart
├── theme/
│   ├── ptc_colors.dart           # ThemeExtension color tokens
│   └── ptc_theme.dart            # Light theme
└── widgets/
    ├── common/                   # TaskTile, ProgressBar
    ├── main_window/              # Scaffold, TitleBar, Sidebar
    ├── views/                    # Dashboard, Period, Settings views
    ├── overlay/                  # CollapsedPill, ExpandedPanel
    └── dialogs/                  # AddTask, QuickAdd dialogs
```

---

## License

MIT License — feel free to use, modify, and distribute. This project is a learning implementation of a todo app concept; it is not proprietary technology.

---

*Built with Flutter • Designed with ❤️ for knowledge workers who never want to forget their plan.*
