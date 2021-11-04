# System Preferences

## First Time Setup

The first thing you should do is update your system. To do that go:
**Apple menu () > About This Mac > Software Update.**

Also upgrade your OS to the latest version to have a more secure OS. macOS
upgrades are usually free so you might as well keep your machine up to date.

If this is a new computer there are a couple tweaks you could make to the
System Preferences. **These settings are all optional, consider them
suggestions. Always choose the setting that makes the most sense to you.**

## Users & Groups

- _Login Options_ -> _Change fast user switching menu as Icon_
- Set up _Password_, _Apple ID_, _Picture_, etc.

## Trackpad

- _Point & Click_
  - Enable _Tap to click with one finger_
  - Change _Secondary click_ to _Right corner_
  - Check Silent Clicking

- _Scroll & Zoom_
  - Uncheck _all_ apart from _Zoom in and out_
  - Uncheck _Rotate with two finders_

- Accessibility > Pointer Control > Mouse & Trackpad
  - Trackpad Options: (Experimenting with this feature) Check enable dragging, three finger drag
  - Trackpad Options: (Experimenting with this feature) Increase scrolling speed to second fastest

## Dock

- _Visual Settings_
  - Reduce dock size to small
  - Check _Magnification_ and reduce size
  - Check _Automatically hide and show the Dock_
- _Other settings_
  - Remove _workspace auto-switching_ by running the following command:

```sh
defaults write com.apple.dock workspaces-auto-swoosh -bool NO
killall Dock # Restart the Dock process
```

## Keyboard
- Key Repeat
  - Turn key repeat all the way to fast
  - Turn delay until repeat all the way to short

- F1, F2 Keys
  - Check _Use F1, F2, etc keys as standard function keys on external keyboards_

## Folder Organization
- New Folders
  - Add new code directory named _dev_ in home directory
  - Add _Screenshots_ folder in Pictures folder

## Finder
- General
  - Change _New finder window show_ to open in your _Home Directory_
- Sidebar
  - Add _Home_ and your _Code Directory_
  - Uncheck all _Shared_ boxes

## Menubar

- Change _battery_ to _Show percentage symbols_ (Dock & Menubar > Battery > _Show Percentage_ 

## Spotlight (Potentially remove)

- Select System Preferences > Spotlight > Search Results, and ensure that Spotlight Suggestions is not enabled.
- (Didn't use, will need to look into) Uncheck _fonts_, _images_, _files_ etc.
- (Didn't use, will need to look into)  Uncheck the _keyboard shortcuts_ as we'll be replacing them with
  [_Alfred_](https://www.alfredapp.com/)

## Accounts

- Add an _iCloud account_ and sync _Calendar_, _Find my Mac_, _Contacts_ etc, 
- Work Computer: turn off Photos

## Security [2][3]

- Security & Privacy > General
  - Set require password to _immediately_ after sleep 
  - **Optional** Use your Apple Watch to unlock apps and your mac
  - Advanced > Check _Require an administrator Password_

- Security & Privacy > FileVault
  - Make FileVault enabled > Select Access via Recovery Key 

- Security & Privacy > Privacy
  - Analytics & Improvements > Uncheck all settings 
  - Apple Advertising: Uncheck personalized ads

## Desktop & Screen Saver

- Screen Saver
  - Set Show screen saver after '5 minutes' 

## User Defaults

- Enable _repeating keys by pressing and holding down keys_: `defaults write
  NSGlobalDomain ApplePressAndHoldEnabled -bool false` (and restart any app
  that you need to repeat keys in)
- Change the _default folder for screenshots_
  - Then run the following command: `defaults write com.apple.screencapture location ~/Pictures/Screenshots/ && killall SystemUIServer`

Sources:

[1] https://sourabhbajaj.com/mac-setup/

[2] https://www.stuartellis.name/articles/mac-setup/

[3] https://github.com/nicolashery/mac-dev-setup
