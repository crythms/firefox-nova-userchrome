# firefox-nova-userchrome

A small `userChrome.css` setup for the Firefox **Nova** UI on Nightly. It does three things:

- **Auto-hides the main toolbar.** The URL bar, bookmarks toolbar, and notification bars slide up out of view, and the page content moves up to fill the space. They slide back down when you hover the tab strip, focus the URL bar, or open a panel.
- **Compacts and darkens the chrome.** Shorter tabs (22px) in a 25px tab strip with tightened margins, and a dark slate accent (`rgb(36,44,59)`) applied to the toolbar, panels, URL bar autocomplete popup, and sidebar.
- **Makes the tab strip translucent (macOS).** The bar the tabs sit in becomes a frosted, slate-tinted pane that blurs whatever is behind the window. The tabs and the nav bar stay opaque. Adjust the tint with the `--uc-tabbar-tint` variable in `userChrome.css`; lower the alpha for more see-through, raise it for more slate.

## Install

1. In `about:config`, set `toolkit.legacyUserProfileCustomizations.stylesheets` to `true`.
   For the frosted tab strip, also set `widget.macos.titlebar-blend-mode.behind-window` to `true`. Without it the strip is a flat system titlebar color instead of a blur of what is behind the window.
2. In `about:profiles`, find your profile's **Root Directory** and open it.
3. Create a `chrome` folder there if it doesn't exist, and copy `userChrome.css` and `autohide_main_toolbar.css` into it.
4. Restart Firefox.

To uninstall, delete the files (or flip the pref back to `false`) and restart.

## Caveats

This targets the Nova redesign on Nightly and leans on internal element IDs, so it can break on any update. If Firefox looks wrong after an upgrade, remove the `chrome` folder first.

The translucent tab strip is macOS only. It reuses the same native titlebar material Firefox draws for its own (pref-gated) native theme, so it can change or stop working when that feature changes.

## License

Mozilla Public License 2.0 — see [LICENSE](LICENSE).

`autohide_main_toolbar.css` is from [MrOtherGuy/firefox-csshacks](https://github.com/MrOtherGuy/firefox-csshacks/tree/master/chrome/autohide_main_toolbar.css), used under the Mozilla Public License 2.0. See that repository for updates and the full license text.
