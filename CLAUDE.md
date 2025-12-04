# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Hidden Bar is a macOS menu bar utility that allows users to hide menu bar items for a cleaner look. It's a native Swift application using AppKit, distributed through the App Store and Homebrew.

## Build Commands

Since this is an Xcode project without command-line build scripts, development is done through Xcode:

- **Open project**: `open "Hidden Bar.xcodeproj"`
- **Build**: Use Xcode's build command (⌘+B) or Product → Build
- **Run**: Use Xcode's run command (⌘+R) or Product → Run
- **Archive for distribution**: Product → Archive

## Architecture

### Two-Target Structure
1. **Hidden Bar** (main app) - The menu bar application
   - Runs as UI element (no dock icon)
   - Bundle ID: `com.dwarvesv.minimalbar`
   - Sandboxed with minimal permissions

2. **LauncherApplication** (helper) - Auto-start functionality
   - Background only helper app
   - Embedded in main app for login item functionality
   - Bundle ID: `com.dwarvesv.LauncherApplication`

### Key Components

**StatusBar Controller** (`hidden/Features/StatusBar/`)
- Core logic for managing menu bar items
- Monitors menu bar changes via timer
- Handles expand/collapse functionality

**Preferences** (`hidden/Features/Preferences/`)
- Settings window implementation
- Global hotkey configuration
- Timer/delay settings

**Models** (`hidden/Models/`)
- `GlobalKeybindingPreferences.swift` - Keyboard shortcut handling
- `SelectedSecond.swift` - Timer configuration

**Localization** - 10 languages supported in `hidden/*.lproj/` directories

### External Dependencies
- **HotKey** (Swift Package Manager) - Global keyboard shortcuts
  - No CocoaPods or Carthage used

## Development Guidelines

### Branch Workflow
- Main branch: `develop` (not master)
- Feature branches: `feature/description`
- Bugfix branches: `bugfix/description`
- Follows git-flow workflow

### Code Organization
- Features are modularized in `hidden/Features/`
- Extensions in `hidden/Extensions/`
- Common utilities in `hidden/Common/`
- Views separated in `hidden/Views/`

### Important Technical Details
- Minimum macOS version: 10.12
- Swift 5.0
- Uses `LSUIElement` (runs as background app)
- Timer-based monitoring for menu bar changes
- Supports both LTR and RTL languages
- App Sandbox enabled with read-only file access

### Testing
No automated tests are configured in this project. Manual testing is required for all changes.

### Distribution
- App Store: Primary distribution method
- Homebrew: `brew install --cask hiddenbar`
- Direct download: GitHub releases
- App is notarized for distribution outside App Store