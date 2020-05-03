---
title: Fether - Frequently Asked Questions
libs:
  faq: true
---

### How to fix a webcam error?

Accounts may be imported into Fether from [Parity Signer](https://github.com/paritytech/parity-signer) if they were created for the chain that you are running with Fether (see FAQ [How to launch Fether on a different network](#how-to-launch-fether-on-a-different-network)).

The webcam on your computer is required for the following reasons:

- Importing an account that was created with Parity Signer
- Signing transactions that are sent using Fether using a Parity Signer account that was imported

If you encounter a webcam error when using Fether, then try the following steps and try using Fether again:

- Check the webcam is connected
- Check the webcam power is turned on
- Check the webcam permissions on your computer
- Restart your computer
- Obtain another webcam

#### macOS

When running Fether in the development environment on macOS Mojave, you need to allow the Terminal application to access your webcam. Try the following steps and try using Fether again:

* Open System Preferences `open '/Applications/System Preferences.app'`
* Open 'Security & Privacy'
* Click 'Privacy' tab
* Click 'Camera' from the list
* Ensure the checkbox for the 'Terminal' application is checked

### Why does the sync starts back at 0% when I restart Fether?

The background process to synchronize the blockchain does not restart from scratch. The sync continues from the point it was left at the last time Fether was launched.

### Why isn't Fether syncing?

In this example we will assume that you have encountered the issue after:

- Starting Fether with the default configuration and it has connected to the Ethereum Mainnet (`foundation`).
- The blockchain database that has been stored on your device has synchronised up to certain block.

You may encounter issues syncing Fether on any network. You know you have the issue due to a corrupt database when:

- In the Fether window on the page with the title "Accounts" it displays "Syncing... foundation" at the bottom left but without showing a percentage progress such as "Syncing... (x%) foundation".
- In the [logs](#how-to-access-logs-to-troubleshoot-errors) the block number that is currently being synced is no longer changing and is not the [latest Ethereum Mainnet block number](https://blockscout.com/eth/mainnet).

To resolve the issue simply delete the corrupted blockchain database for that network in the [subdirectory where the light client blockchain database used by Fether is stored](#where-is-the-light-client-blockchain-database-used-by-fether-stored). Then restart Fether and it will start synchronizing with that network from scratch.

### How to add my ERC-20 Token to Fether?

We use the following repository to get the token list: [https://github.com/ethereum-lists/tokens](https://github.com/ethereum-lists/tokens).
To see your token in Fether, you need first to open a pull request to this repository. Once it is merged it will be added in Fether's next release.

### Why doesn't a token have an icon?

We use the following repository to get the token list: [https://github.com/ethereum-lists/tokens](https://github.com/ethereum-lists/tokens).
If you don't see an image for a token in Fether, it means that the `logo` field for this token was left empty or the url given is not reachable. Either way, you need to open a pull request or an [issue](https://github.com/ethereum-lists/tokens/issues/new) to this repository to fix it. Once it is merged it will be added in Fether's next release.

### Where are Fether accounts stored?

Keys for Fether accounts are stored in chain-specific subdirectories within the Parity Ethereum 'keys' folder. You will find them here:

- macOS: `~/Library/Application\ Support/io.parity.ethereum/keys`
- Linux: `$HOME/.local/share/io.parity.ethereum/keys`
- Windows 7/10: `%HOMEPATH%/AppData/Roaming/Parity/Ethereum/keys`

### How to delete an account in Fether?

We chose not to allow the deletion of accounts from the Fether user interface. In case you really know what you are doing and do not want an account to appear in Fether, you can locate and move the keystore file from the 'keys' folder. You will find them here: [Where are Fether accounts stored errors](#where-are-fether-accounts-stored).

### Where is Fether installed?

Fether binary executable files are stored here:

- macOS: `/Applications/Parity Fether.app/Contents/MacOS/Parity Fether`
- Linux:
  - `.deb`
    - Parity Fether: `/opt/Parity\ Fether/fether`
  - AppImage
    - Parity Fether: `/wherever_you_store_it/Parity\ Fether\ X.X.X.AppImage`
  - binary
    - Parity Fether: `/wherever_you_store_it/fether`
- Windows:
  - Parity Fether: `C:\Users\fether\AppData\Local\Programs\fether\fether`

### Where is the light client blockchain database used by Fether stored?

Light client blockchain databases for Fether are stored in chain-specific subdirectories within the Parity Ethereum 'chains_light' folder. You will find them here:

- macOS: `~/Library/Application\ Support/io.parity.ethereum/chains_light`
- Linux: `$HOME/.local/share/io.parity.ethereum/chains_light`
- Windows 7/10: `%HOMEPATH%/AppData/Roaming/Parity/Ethereum/chains_light`

### Where are Fether logs stored?

- macOS: `~/Library/Application\ Support/fether/fether.log`
- Linux: `~/.config/fether/fether.log`
- Windows: `"C:\Windows\Users\<YOUR_USERNAME>\Application/ Data\fether\fether.log"`

### Where is Parity Ethereum installed?

- macOS: `/Applications/Parity Ethereum.app/Contents/MacOS/parity`
- Linux:
  - `.deb`
    - Parity Ethereum: `/opt/Parity Fether/resources/static/parity`
    - Parity Ethereum chain: `~/.local/share/io.parity.ethereum/`
  - AppImage
    - Parity Ethereum: `/tmp/.mount_Parity[something]/resources/static/parity`
    - Parity Ethereum chain: `~/.local/share/io.parity.ethereum/`
  - binary
    - Parity Ethereum: `/wherever_you_store_it/resources/static/parity`
    - Parity Ethereum chain: `~/.local/share/io.parity.ethereum/`
- Windows:
  - Parity Ethereum:
    - `C:\Program Files\Parity Technologies\Parity\parity.exe`
    - `C:\Users\fether\AppData\Local\Programs\fether\resources\static\parity`
  - Parity Ethereum chain: `C:\Users\fether\AppData\Roaming\Parity\Ethereum\`

Note that with older versions of Fether (i.e. <0.3) or separately installed versions of Parity Ethereum then it may be installed at:

- Linux:
  - binary
    - Parity Ethereum: `/bin/parity`, `/usr/bin/parity`, or `/usr/local/bin/parity`
- Windows:
  - Parity Ethereum: `C:\Program Files\Parity Technologies\Parity\parity.exe`

### How to launch Fether on a different network?

You can pass specific flags (such as `--chain`) for Fether to launch the underlying Parity Ethereum on a specific network:

```bash
# Launching Fether with a Parity Ethereum light client node on Ropsten
$ /path/to/fether --chain ropsten --light
```

Fether only supports networks that are compatible with running a light client node using the `--light` option of the Fether CLI that is shown above, and as mentioned in the FAQ [What networks are supported by Fether?](#what-networks-are-supported-by-fether?).

### What networks are supported by Fether?

Fether currently supports: 
- Ethereum Mainnet
- Ethereum Classic
- Kovan Testnet
- Ropsten Testnet

Görli Testnet support will be added soon.

Read here about [how to launch Fether on a different network](#how-to-launch-fether-on-a-different-network).

### How to launch Fether with a separately launched Parity Ethereum node?

Fether will download and install Parity Ethereum if it is not already installed. Fether will run a Parity Ethereum light client node if Parity Ethereum has not already been launched separately.

1) Launch a Parity Ethereum node using any appropriate flags. Check what flags are available with `parity --help`).

```bash
# Launch a Parity Ethereum light client node on the Ropsten network instead of the Kovan (default) test network
$ parity --chain ropsten --light
```

2) Launch Fether (using the launcher menu or in a terminal session), it will automatically detect the local node and connect to it.

### How to connect Fether to a Parity Ethereum full node?

Fether will automatically connect to any Parity Ethereum node that is already running (using WebSockets port 8546).
To connect Fether to a full node:

1) Launch a Parity Ethereum full node using any appropriate flags. Check what flags are available with `parity --help`).

```bash
# Launch a Parity Ethereum full node on Ropsten test network
$ parity --chain ropsten
```

2) Launch Fether (from the application launcher menu or in a terminal session), it will automatically detect the local node and connect to it.

### How to access logs to troubleshoot errors?

To help users understand what is going on if Fether crashes, it is essential to provide logs.

Logs for the user interface (UI) may be viewed as follows:
- Open the Fether menu by right-clicking the Fether window
- Click the menu item "View > Toggle Developer Tools"
- Undock the Developer Tools into a separate window
  - Clicking the '3 dots' icon located at the top right
  - Select the 'separate windows' symbol
- Click the 'Console' tab in the Developer Tools window
- Expand the 'Console' tab so it is large enough to take a screenshot of any logs, warnings, or errors.
- Please take a screenshot of the Fether window and the logs and share them with us by posting an [Issue](https://github.com/paritytech/fether/issues) in the Fether GitHub repository or by clicking the 'Feedback' button on the Accounts page of the Fether window.

Logs related to the underlying Parity Ethereum node or the overall Fether application will only appear if you launch Fether using a terminal session.

Logs that are generated when running Fether are saved at locations mentioned in FAQ [Where are Fether logs stored?](#where-are-fether-logs-stored?). Please share the log file with us by uploading it when creating an [Issue](https://github.com/paritytech/fether/issues) in the Fether GitHub repository or by clicking the 'Feedback' button on the Accounts page of the Fether window.

#### Tips

If you want the Developer Tools to automatically open each time you run Fether, see the FAQ "How to open Developer Tools automatically when Fether launches".

#### Advanced

If you want to monitor the latest changes to the log file whilst running Fether in a terminal session then use the `tail` command (i.e. run `tail -f ~/.config/fether/fether.log`).

If you want to troubleshoot errors in the user interface (UI) whilst running Fether then add [line-of-code breakpoints](https://developers.google.com/web/tools/chrome-devtools/javascript/breakpoints) in Developer Tools by clicking the 'Sources' tab, choosing 'Page > top > webpack-internal://', and then setting line-of-code breakpoints.

### What is "taskbar mode"?

Fether runs by default as a [tray](https://electronjs.org/docs/api/tray) application that is [frameless](https://electronjs.org/docs/api/frameless-window#frameless-window), so it doesn't have any window decoration (basically a frame and the usual minimize/full screen/close buttons)

Below we describe whether Fether's features that are 'Always' apparent, or only apparent depending on whether taskbar mode is 'Enabled' or 'Disabled', and depending on which operating system Fether is run on.

#### macOS

Taskbar mode is `true` by default.

* **Enabled** `true`
  * Tray icon - Left-click or right-click the tray icon shows "tray context menu" containing just "Show/Hide Fether" and "Quit" options. "Show/Hide Fether" toggles the Fether window show/hide. It includes the "Reload" option only when run in the development environment, since it is necessary to reload the Fether window when it is launched using `yarn start`. 
  * Dock icon - no action
  * Fether window - frameless
* **Disabled** `false`
  * Dock icon - toggles show/hide Fether window
  * Fether window - frame (with close/minimise icons)
* **Always**
  * Menubar - Fether menu shown by default
  * Fether window - "window context menu" shown upon right-click in the Fether window
  * Fether window - position is saved upon moving, minimising, or closing so it is restored in the same position.

#### Linux

Taskbar mode is `true` by default.

* **Enabled** `true`
  * Tray icon - Left-click or right-click the tray icon shows "tray context menu" containing just "Show/Hide Fether" and "Quit" options. "Show/Hide Fether" toggles the Fether window show/hide. It includes the "Reload" option only when run in the development environment, since it is necessary to reload the Fether window when it is launched using `yarn start`.
  * Dock icon - toggles show/hide Fether window
  * Fether window - frameless
* **Disabled** `false`
  * Dock icon - toggles show/hide Fether window
  * Fether window - frame (with close/minimise icons)
  * Menubar - Fether menu may not be shown in the tray by default depending on whether [`setMenuBarVisibility`](https://electronjs.org/docs/api/browser-window#winsetmenubarvisibilityvisible-windows-linux) has been set. Fether menu may be configured to automatically hide by setting [`setAutoHideMenuBar`](https://electronjs.org/docs/api/browser-window#winsetautohidemenubarhide). Toggle show/hide the Fether menu in the frame by clicking the Fether window and then holding down the ALT key to reveal it, which only works if auto-hide menu bar is enabled.
* **Always**
  * Fether window - "window context menu" shown upon right-click in the Fether window
  * Fether window - position is saved upon moving, minimising, or closing so it is restored in the same position.

#### Windows

Taskbar mode is `true` by default.

* **Enabled** `true`
  * Tray icon - Left-click toggles show/hide Fether window
  * Tray icon - Right-click the tray icon shows "tray context menu" containing just "Show/Hide Fether" and "Quit" options. "Show/Hide Fether" toggles the Fether window show/hide. It includes the "Reload" option only when run in the development environment, since it is necessary to reload the Fether window when it is launched using `yarn start`.
  * Dock icon - toggles show/hide Fether window
  * Fether window - frameless
* **Disabled** `false`
  * Dock icon - toggles show/hide Fether window
  * Fether window - frame (with close/minimise icons).
  * Menubar - Fether menu may not be shown in the tray by default depending on whether [`setMenuBarVisibility`](https://electronjs.org/docs/api/browser-window#winsetmenubarvisibilityvisible-windows-linux) has been set. Fether menu may be configured to automatically hide by setting [`setAutoHideMenuBar`](https://electronjs.org/docs/api/browser-window#winsetautohidemenubarhide). Toggle show/hide the Fether menu in the frame by clicking the Fether window and then holding down the ALT key to reveal it, which only works if auto-hide menu bar is enabled.
* **Always**
  * Fether window - "window context menu" shown upon right-click in the Fether window
  * Fether window - position is saved upon moving, minimising, or closing so it is restored in the same position.

### How to run Fether without "taskbar mode"?

#### Development Environment

Disable the `TASKBAR` environment variable prior to launching Fether as follows:

```bash
TASKBAR=false yarn start
```

### How to open Developer Tools automatically when Fether launches?

#### Development Environment

Open Developer Tools automatically by running Fether with the `DEBUG` environment variable set as follows:

```bash
DEBUG=true yarn start
```

### What to do if the Fether window appears unresponsive or does not load?

#### Development Environment

If you run Fether with `yarn start` it is a known issue that the Fether window will hang with just a white/blank screen even after it has compiled successfully. Fix it by simply right-clicking the Fether window to reveal the Fether menu, and choose the menu item 'View > Reload' (or use shortcut CMD + R on macOS, CTRL + R on Linux/Windows). Alternatively run Fether with `yarn electron` (without live reload).

If Fether is otherwise unresponsive or does not load then please follow the steps in the FAQ [How to access logs to troubleshoot errors](#how-to-access-logs-to-troubleshoot-errors).

#### Production Environment

Please follow the steps in the FAQ [How to access logs to troubleshoot errors](#how-to-access-logs-to-troubleshoot-errors).

### How to switch between languages that Fether supports?

In the Fether window you can switch between supported languages by simply right-clicking the Fether window to reveal the Fether menu, then choosing the menu item 'Preferences > Language', and selecting one of the available languages from the list (i.e. English).

The Fether window will then automatically refresh and its contents will now be in the language you chose. The active language that you chose will now have a tick next to it in the menu.

### How to add support for a new language to Fether?

Contributors are invited to create a Pull Request that translates Fether other languages.

English language support is currently the default.

#### Example: Add language support for the German language

**Solution:** See the following Pull Request that shows the changes that were required to add German language support https://github.com/paritytech/fether/pull/464


1) Find the [internationalisation abbreviation](https://www.w3.org/International/O-charset-lang.html) of the new language that you want to add. In this example the new language will be referred to as <LANG>. Example: 'de' for Deutsch (German), or 'en' for English. So if you wanted to add the French language then <LANG> would be 'fr'.
2) Convert the Fether menu into the new language as follows.
* Create a file named <LANG>.json within the fether-electron folder. Example: fether-electron/src/main/app/menu/i18n/locales/de.json.
* Copy and paste into that file the contents of the existing English file that is located in fether-electron/src/main/app/menu/i18n/locales/en.json.
* Find someone who is a native speaker of the new language to translate each **'value'** (DO NOT translate the 'keys', they must remain in English) into the new language.
* Update fether-electron/src/main/app/menu/i18n/locales/index.js. See how it was done in the 'Solution' mentioned above.
* Update fether-electron/src/main/app/menu/template/index.js:
  * Add an item for the new language as a value of the `submenu`.
* Update fether-electron/src/main/app/menu/i18n/index.js:
  * Import the <LANG> that you added in the 'locales' subdirectory.
  * Add the new language as a fallback language in the desired order to the `fallbackLng`.
  * Add a key named <LANG> to `resources` using the imported <LANG>.json file as the namespace.
3) Language conversion of the Fether window contents to the new language.
* Create a file named <LANG>.json within the fether-react folder. Example: fether-react/src/i18n/locales/de.json. Copy/paste into it the contents of the English file fether-react/src/i18n/locales/en.json. Find a native speaker in that language to convert each **value** (not key) into the new language.
* Update fether-react/src/i18n/locales/index.js.
* Update fether-react/src/i18n/index.js, which includes:
  * Import the <LANG> from the 'locales' subdirectory.
  * Adding the new language as a fallback language in the desired order to the [`fallbackLng`](https://www.i18next.com/principles/fallback#fallback-language).
  * Add a subkey named <LANG> under the `resources` key using the imported <LANG>.json file as the namespace. See how it was done in the 'Solution' mentioned above.

#### Limitations

* After choosing a new language to switch to, the Fether window will refresh automatically and the contents of Fether will now be in the new language, **except** for the menu items "Show/Hide Fether" and "Quit" that are shown when you click the taskbar icon. These menu items will only change to the language that you chose after you **restart** Fether.

* The Fether Terms & Conditions are only available in English.

* Full support for translating the UI is provided, however only limited support is provided for translating the logs is provided. For example the following files are not translated:
  * fether-electron/src/main/app/menu/i18n/index.js
  * fether-react/src/i18n/index.js
  * fether/scripts/fetch-latest-parity.js
