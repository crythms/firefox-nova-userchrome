# firefox-nova-userchrome

A small `userChrome.css` setup for the Firefox **Nova** UI (Firefox 158 or later). It does two things:

- **Puts the tabs and the toolbar on one row**, laid out like the Helium browser: window controls, back, forward, reload, the URL bar, then the tabs and the new-tab button, then your extension buttons and the menu on the right. The URL bar takes about 30% of the window, and tabs are as tall as the URL bar. Customize Toolbar, vertical tabs, and popup windows keep Firefox's normal two rows.
- **Darkens the chrome.** A near-black accent (`rgb(30,32,32)`) applied to the toolbar, panels, URL bar autocomplete popup, and sidebar.

The dark colors only apply with the default theme. Pick any other theme (Dark, Light, Alpenglow, or one from the theme picker or AMO) and Firefox uses that theme's colors instead. The one-row layout stays on either way.

## Install

1. In `about:config`, set `toolkit.legacyUserProfileCustomizations.stylesheets` to `true`.
2. In `about:profiles`, find your profile's **Root Directory** and open it.
3. Create a `chrome` folder there if it doesn't exist, and copy `userChrome.css` and `one_line_toolbar.css` into it. If an `autohide_main_toolbar.css` from an older version is there, you can delete it.
4. Restart Firefox.

To uninstall, delete the files (or flip the pref back to `false`) and restart.

## Tweaks

To change the URL bar width or the narrowest the tab area may get, override these in a `:root { }` rule after the `@import` in `userChrome.css`:

```css
:root {
  --uc-urlbar-width: clamp(176px, 30vw, 640px);
  --uc-tab-slot-min-width: 160px;
}
```

The Sidebar and List all tabs (⌄) buttons aren't part of Helium's layout. Right-click the toolbar, choose **Customize Toolbar…**, and drag them off if you don't want them. Any flexible spaces in the toolbar are hidden on the single row.

## Caveats

This targets the Nova redesign and leans on internal element IDs (`#vertical-spacer`, `#urlbar-container`, `#TabsToolbar`) and CSS anchor positioning, so it can break on any update. If Firefox looks wrong after an upgrade, remove the `chrome` folder first.

## License

Mozilla Public License 2.0 — see [LICENSE](LICENSE).
