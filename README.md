# layer-xterm

The classic xterm X terminal emulator for OpenCharly desktop images.

The `xterm` candy installs `xterm`, the reference X terminal emulator (usable
under XWayland). On labwc (`selkies-desktop`), launching xterm triggers XWayland
to start on demand, which enables the X11-based automation tools (`xdotool`,
`xprop`, `xwininfo`) to find windows.

## What it provides

| Property | Value |
|---|---|
| Layer / candy | `xterm` |
| Package | `xterm` (arch / fedora) |
| Binary | `/usr/bin/xterm` |
| WM_CLASS | `xterm` / `XTerm` |
| XWayland | triggers on-demand start on labwc |
| Service / port | none |

## How to use it

Compose the layer by pinning this repo in a box's `candy:` list — typically
transitively through the `selkies-desktop` metalayer:

```yaml
my-desktop-box:
  candy:
    base: fedora
    candy:
      - '@github.com/opencharly/layer-xterm:v2026.239.1631'
```

Drive xterm through the `wl:` verb's methods (run with `charly check live <image>
--filter wl`): `wl: exec` launches it (triggering XWayland, with `DISPLAY=:0` set
automatically), `wl: focus` focuses it by app_id, and `wl: geometry` reports its
window geometry.

The candy's `plan:` asserts the binary at `/usr/bin/xterm` and the package
registered.

## Layout

- `charly.yml` — the `xterm:` candy entity (the per-distro packages, the
  `check:` assertions) and the embedded `xterm-skill:` skill entity.
- `.github/workflows/tag-on-merge.yml` — CalVer tag + `CHANGELOG/` on merge.
- `README.md` — this user overview.

## Related

- Owning skill: `/charly-selkies:xterm`
- `/charly-check:wl` — the `wl:` verb's exec / focus / close / xprop / geometry methods
- `/charly-selkies:selkies-desktop-layer` — desktop metalayer that includes this candy
- [`opencharly/charly`](https://github.com/opencharly/charly) — the charly CLI and image builder
- [`opencharly/opencharly`](https://github.com/opencharly/opencharly) — the umbrella
