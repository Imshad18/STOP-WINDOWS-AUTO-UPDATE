# STOP WINDOWS AUTO UPDATE

A simple Windows CMD script that blocks automatic Windows Update downloads and installs by applying Windows Update policy settings and disabling related update services.

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

Windows feature upgrades, repair installs, policy changes, or future Windows servicing changes can potentially overwrite update settings. Re-run the script if Windows restores automatic update behavior.

Disabling Windows Update also stops automatic security and reliability updates, so only use this if you intend to manage updates manually.
