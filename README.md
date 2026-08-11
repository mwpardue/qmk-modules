# @mwpardue's QMK community modules (fork of @getreuer's)

(This is not an officially supported Google product.)

This is a personal fork of [getreuer/qmk-modules](https://github.com/getreuer/qmk-modules)
by Pascal Getreuer, maintained by Matthew Pardue (@mwpardue) for use in my own
QMK keymap. It combines Pascal's modules with additional modules from other
authors and some of my own. See [NOTICE](./NOTICE) for full attribution and
licensing details — several modules below are **not** covered by this repo's
top-level Apache-2.0 license.

![](doc/banner.jpg)

| Module                                    | Description                                           | Source |
|-------------------------------------------|--------------------------------------------------------|--------|
| [Achordion](./achordion/)                 | Customize the tap-hold decision.                        | getreuer |
| [Casemodes](./casemodes/)                 | XCase / case-mode word transforms.                       | Andrew Rae (@andrewjrae) |
| [Custom Shift Keys](./custom_shift_keys/) | Customize what keycode is produced when shifted.        | getreuer |
| [Keycode String](./keycode_string/)       | Format QMK keycodes as human-readable strings.           | getreuer |
| [Mouse Turbo Click](./mouse_turbo_click/) | Click the mouse rapidly.                                 | getreuer |
| [Orbital Mouse](./orbital_mouse/)         | A polar approach to mouse key control.                   | getreuer |
| [PaletteFx](./palettefx/)                 | Palette-based animated RGB matrix lighting effects.      | getreuer |
| [Select Word](./select_word/)             | Convenient word and line selection.                      | getreuer |
| [Sentence Case](./sentence_case/)         | Automatically capitalize sentences.                      | getreuer |
| [Smart Select](./smart_select/)           | Personal word/line selection helper.                     | mwpardue |
| [SOCD Cleaner](./socd_cleaner/)           | SOCD filtering for fast gaming inputs.                   | getreuer |
| [Tap Flow](./tap_flow/)                   | Disable HRMs during fast typing (Global Quick Tap).      | getreuer |


## What is this?

Most of the modules here are Pascal Getreuer's community modules for
[Quantum Mechanical Keyboard (QMK)](https://docs.qmk.fm) firmware — see his
[original repo](https://github.com/getreuer/qmk-modules) and
[his QMK keymap](https://github.com/getreuer/qmk-keymap). This fork adds
`casemodes` (by Andrew Rae) and `smart_select` (my own) for use in my
personal keymap.


## License

Most of this repo uses the Apache License 2.0, inherited from the upstream
[getreuer/qmk-modules](https://github.com/getreuer/qmk-modules) repo — see the
[LICENSE file](LICENSE.txt) for the full text. **This repo also contains code
under other licenses; see [NOTICE](./NOTICE) and the header comments in each
module for the authoritative license governing that module.** In particular,
`casemodes/` is licensed GPL-2.0-or-later by its original author, Andrew Rae,
not Apache-2.0.


## How to install

This repo makes use of [Community
Modules](https://getreuer.info/posts/keyboards/qmk-community-modules/index.html)
support added in QMK Firmware 0.28.0, released on 2025-02-27. [Update your QMK
set
up](https://docs.qmk.fm/newbs_git_using_your_master_branch#updating-your-master-branch)
to get the latest. If you have it, there will be a `modules` folder inside your
`qmk_firmware` folder.

**Step 1. Download modules.** Run these shell commands to download the
modules, replacing `/path/to/qmk_firmware` with the path of your
"`qmk_firmware`" folder:

```sh
cd /path/to/qmk_firmware
mkdir -p modules
git submodule add https://github.com/mwpardue/qmk-modules.git modules/mwpardue
git submodule update --init --recursive
```

Or if using [External
Userspace](https://docs.qmk.fm/newbs_external_userspace), replace the first
line with `cd /path/to/your/external/userspace`.

Or if you don't want to use git, download a .zip of this repo from its GitHub
page into the `modules` folder. Unzip it, then rename the resulting folder to
`mwpardue`.

If you only want Pascal Getreuer's original modules without this fork's
additions, use his repo directly instead:
[github.com/getreuer/qmk-modules](https://github.com/getreuer/qmk-modules).

In any case, the installed directory structure is like this:

    <QMK_FIRMWARE or QMK_USERSPACE>
    └── modules
        └── mwpardue
            ├── achordion
            ├── casemodes
            ├── custom_shift_keys
            ├── keycode_string
            ├── smart_select
            └── ...

**Step 2. Add modules to keymap.json.** Add a module to your keymap by writing a
file `keymap.json` in your keymap folder with the content

```json
{
  "modules": ["mwpardue/tap_flow"]
}
```

Or if a `keymap.json` already exists, merge the `"modules"` line into it. Add
multiple modules like:

```json
{
  "modules": ["mwpardue/tap_flow", "mwpardue/sentence_case"]
}
```

Follow the modules' documentation for any further specific set up.

**Step 3. Update the firmware.** Compile and flash the firmware as usual. If
there are build errors, try running `qmk clean` and compiling again for a clean
build.


## How to uninstall

Remove the modules from `keymap.json` and delete the `modules/mwpardue` folder.

