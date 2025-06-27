# 🚀 niripwmenu

<p align="center">
  <img src="https://raw.githubusercontent.com/antrax2024/niripwmenu/refs/heads/main/src/niripwmenu/assets/banner.jpg" alt="niripwmenu Logo">
</p>

<div align="center">
  <span>
    <img alt="PyPI - Version" src="https://img.shields.io/pypi/v/niripwmenu">
    <img alt="AUR Version" src="https://img.shields.io/aur/version/niripwmenu">
    <img alt="Python Version from PEP 621 TOML" src="https://img.shields.io/python/required-version-toml?tomlFilePath=https%3A%2F%2Fraw.githubusercontent.com%2Fantrax2024%2Fniripwmenu%2Frefs%2Fheads%2Fmain%2Fpyproject.toml">
    <img alt="GitHub last commit" src="https://img.shields.io/github/last-commit/antrax2024/niripwmenu">
    <img alt="PyPI - Wheel" src="https://img.shields.io/pypi/wheel/niripwmenu">
</span>
</div>

A modern powermenu for [Niri Scrollable-Tiling Wayland compositor.](https://github.com/YaLTeR/nirihttps:/)

## 📖 Overview

**niripwmenu** provides a sleek graphical interface for system operations (_shutdown, reboot, and logoff_) in [Niri Scrollable-Tiling Wayland compositor.](https://github.com/YaLTeR/nirihttps:/) Built with Python and Gtk4, it offers extensive customization through configuration files and CSS styling.

## Installation

### Install with pip

```bash
pip install niripwmenu
```

### Install with AUR

**niripwmenu** is available in [AUR](https://aur.archlinux.org/).

```bash
paru -S niripwmenu
# or
yay -S  niripwmenu
```

## 🛠️ Usage

```bash
$ niripwmenu
```

If the configuration or style files don't exist at the XDG_CONFIG_PATH (**/home/your_username/.config/niripwmenu**), **niripwmenu** will attempt to create default versions.

## ⚙️ Configuration (`config.yaml`)

The behavior and appearance of niripwmenu is controlled via a YAML configuration file (default: `~/.config/niripwmenu/config.yaml`).

### Configuration Structure

The configuration file defines a list of buttons with their properties:

```yaml
buttons:
  - icon_path: "/path/to/icon.png" # Path to PNG icon file
    id: "buttonId" # CSS identifier for styling
    hint: "Tooltip text" # Text shown on hover
    command: "system_command" # Command executed when clicked
```

### Button Properties

Each button supports the following properties:

- **`icon_path`** (string): Absolute path to a PNG image file used as the button icon
- **`id`** (string): Unique identifier used for CSS styling and element identification
- **`hint`** (string): Text displayed as tooltip when user hovers over the button
- **`command`** (string): Shell command that will be executed when the button is clicked

### Default Configuration

The default configuration includes three standard power menu actions:

- **Power Off**: Executes `poweroff` command
- **Restart**: Executes `reboot` command
- **Logout**: Executes `hyprctl dispatch exit` for Hyprland session exit

### Custom Commands

You can customize the commands to suit your system setup. For example:

- Use `systemctl poweroff` instead of `poweroff`
- Add custom scripts: `/path/to/custom/script.sh`
- Use different logout commands for other window managers

If the configuration file doesn't exist, niripwmenu will create a default version automatically.

## 🎨 Styling (`style.css`)

The visual appearance of niripwmenu is controlled via a CSS file (default: `~/.config/niripwmenu/style.css`).

### Key Customizable Elements

#### **Window Container**

- **`window`**: Styles the main application window
  - Background color, border styling, border radius
  - Minimum dimensions (width/height)
  - Default: Black background (`#000000`) with green border (`#40a02b`)

#### **Button Base Styling**

- **`button`**: Base style for all action buttons
  - Background, border, padding, dimensions
  - Border radius for rounded corners
  - Default: Black background, no border, `120x120px` minimum size, `10px` border radius

#### **Button Interaction States**

Individual buttons have specific styling for hover, active, focus, and checked states:

- **`button#buttonPowerOff`**: Power off button interactions
  - Default: Red border (`#e64553`) on interaction
- **`button#buttonRestart`**: Restart button interactions
  - Default: Blue border (`#04a5e5`) on interaction
- **`button#buttonLogout`**: Logout button interactions
  - Default: Orange border (`#df8e1d`) on interaction

#### **Button Icons**

- **`button image`**: Styles the icon images within buttons
  - Background color matching the window theme

#### **Hint Label**

- **`label#hint_label`**: Styles the tooltip/hint text display
  - Font family, color, size, weight, and positioning
  - Default: "Hack Nerd Font Mono", cyan color (`#209fb5`), `24px` size

### Default Color Scheme

The default theme uses a dark color palette:

- **Background**: Black (`#000000`)
- **Window Border**: Green (`#40a02b`)
- **Power Off**: Red (`#e64553`)
- **Restart**: Blue (`#04a5e5`)
- **Logout**: Orange (`#df8e1d`)
- **Hint Text**: Cyan (`#209fb5`)

### Custom Styling

You can completely customize the appearance by:

1. Modifying the default `~/.config/niripwmenu/style.css`
2. Using the `-s` command-line option to specify a custom CSS file
3. Adjusting colors, fonts, sizes, borders, and animations

The CSS follows standard GTK4 styling conventions, allowing for extensive customization of the user interface.

## 🔤 Keyboard Navigation

**niripwmenu** `block` keyboard when execute and only release after the user choose one button (action) or quit **niripwmenu**.
The app supports keyboard navigation for quick access without using the mouse:

### Navigation

- **Right Arrow (→)**: Select the next button
- **Left Arrow (←)**: Select the previous button
- **Enter**: Execute the command of the currently selected button
- **q** or **ESC**: Quit application

### Usage Tips

- Use the arrow keys to cycle through available power menu options
- The currently selected button will be highlighted with a colored border
- Press Enter to confirm and execute the selected action
- You can quickly navigate and execute commands using only the keyboard

This keyboard navigation makes niripwmenu accessible and efficient for power users who prefer keyboard shortcuts over mouse interaction.

**niripwmenu** supports keyboard navigation for quick access without using the mouse:

This keyboard navigation makes niripwmenu accessible and efficient for power users who prefer keyboard shortcuts over mouse interaction.

## 🔗 Integration with Niri

To launch niripwmenu using a keybinding in [Niri](https://github.com/YaLTeR/nirihttps:/), add a keybind in your `config.kdl`:

```ini
Mod+P { spawn "niripwmenu"; }
```

## 📜 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

```
MIT License

Copyright (c) 2023 niripwmenu Contributors

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```
