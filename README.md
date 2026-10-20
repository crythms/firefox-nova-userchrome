# firefox-nova-userchrome

A small `userChrome.css` setup for the Firefox **Nova** UI on Nightly. It does two things:

- **Auto-hides the main toolbar.** The URL bar, bookmarks toolbar, and notification bars slide up out of view, and the page content moves up to fill the space. They slide back down when you hover the tab strip, focus the URL bar, or open a panel.
- **Compacts and darkens the chrome.** Shorter tabs (22px) in a 25px tab strip with tightened margins, and a near-black accent (`rgb(30,32,32)`) applied to the toolbar, panels, URL bar autocomplete popup, and sidebar. On macOS the tab strip gets it too.

The dark colors only apply with the default theme. Pick any other theme (Dark, Light, Alpenglow, or one from the theme picker or AMO) and Firefox uses that theme's colors instead. The compact sizing and auto-hiding toolbar stay on either way.

## Install

1. In `about:config`, set `toolkit.legacyUserProfileCustomizations.stylesheets` to `true`.
2. In `about:profiles`, find your profile's **Root Directory** and open it.
3. Create a `chrome` folder there if it doesn't exist, and copy `userChrome.css` and `autohide_main_toolbar.css` into it.
4. Restart Firefox.

To uninstall, delete the files (or flip the pref back to `false`) and restart.

## Caveats

This targets the Nova redesign on Nightly and leans on internal element IDs, so it can break on any update. If Firefox looks wrong after an upgrade, remove the `chrome` folder first.

## License

Mozilla Public License 2.0 — see [LICENSE](LICENSE).

`autohide_main_toolbar.css` is from [MrOtherGuy/firefox-csshacks](https://github.com/MrOtherGuy/firefox-csshacks/tree/master/chrome/autohide_main_toolbar.css), used under the Mozilla Public License 2.0. See that repository for updates and the full license text.
