# STOP WINDOWS AUTO UPDATE

Disables automatic Windows Update downloads and blocks Windows from connecting to Microsoft Windows Update servers using policy and service settings.

## Usage

1. Download `Disable_Windows_Auto_Updates.cmd`.
2. Right-click the file.
3. Select **Run as administrator**.
4. Let the script finish.
5. Restart Windows.

## What it changes

The script:

- Sets `NoAutoUpdate = 1`.
- Blocks connections to normal Microsoft Windows Update locations.
- Redirects Windows Update to blank WSUS addresses.
- Stops and disables:
  - Windows Update (`wuauserv`)
  - Update Orchestrator (`UsoSvc`)
  - Windows Update Medic (`WaaSMedicSvc`)
- Forces the related service startup values to disabled.
- Runs `gpupdate /force`.
- Prints verification output before exiting.

## Important

Run the script as Administrator.

This is designed to stop normal automatic Windows Update downloading and installation. It is not a guarantee that Windows can never change these settings. Major Windows upgrades, repair installs, administrator or organization policies, or future servicing changes can overwrite them. If Windows restores automatic update behavior, run the script again.

Disabling Windows Update also stops automatic security and reliability updates, so use this only if you intend to manage updates manually.
