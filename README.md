# SSSM - Simple Steam Skin Manager
A simple skin manager for Steam on Linux that can install, upgrade and uninstall skins from a CLI environment.
Mostly meant to be used with a package manager in order to automatically install, upgrade and uninstall a skin as the skin's package is installed, upgraded or uninstalled.

This is necessary because Steam creates a `~/.local/share/Steam` directory for each user, meaning that package managers can't properly install Steam skins.

## Commands
Syntax: sssm <action> [action-specific arguments]

Actions:
- list [user]

  Lists all currently installed skins.

  Parameters:
    - user (optional): If specified, list only the skins that user has installed. Otherwise, list all globally installed skins.
- sync <skin> [user]

  Installs or upgrades a skin for a user.

  Parameters:
    - skin: The skin to install / upgrade.
    - user (optional): The user to install / upgrade the skin for. If left empty, install / upgrade for all users.
- remove <skin> [user]

  Uninstalls a skin for a user.

  Parameters:
    - skin: The skin to uninstall.
    - user (optional): The user to uninstall the skin for. If left empty, uninstall for all users.
- version

  Prints the manager's version and exits.

## Directories
- `/usr/share/steam/skins`
    - SSSM looks for installed skins here. They will then be copied to the user's steam installation directory (see below). In other words, this is where the package manager should place installed skins.
- `/home/*/.local/share/Steam/skins`
    - This is where copies of the installed skins will be placed for each user.

## Typical Usage
- After installation of a skin:

    `sssm sync <skin_name>`

- After a skin has been upgraded:

    `sssm sync <skin_name>`

- After a skin has been uninstalled:

    `sssm remove <skin_name>`

- To list installed skins:

    `sssm list`

## License
SSSM is licensed under the MIT license. See [LICENSE](LICENSE) for the full license text.
