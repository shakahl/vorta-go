# Vorta-Go

An implementation of [Vorta](https://github.com/borgbase/vorta) in Golang to improve deployment and packaging.

Work in progress and NOT functional. Use the [Python version](https://github.com/borgbase/vorta) if you need something that works.

## Progress

Borg Commands:
- [x] `init`
- [x] `create`
- [x] `info`
- [x] `check`
- [ ] `extract`
- [ ] `mount`
- [ ] `delete`
- [ ] `diff`
- [ ] `list-archive`
- [ ] `list-repo`
- [ ] `prune`
- [ ] `umount`
- [x] `version`

Backend Functionality
- [x] Keychain/SecretService
- [x] Background scheduler
- [x] Single App
- [ ] Backup status (icon, menu)
- [x] Read and parse existing SSH keys
- [x] Create new SSH key
- [x] Check Borg version for available features
- [ ] Tests
- [ ] Read list of WiFis
- [ ] Password fallback in database
- [ ] Translations

Packaging (via Docker)
- [x] macOS
- [x] Ubuntu 19.04
- [ ] Debian 10
- [ ] Fedora 30
- [x] Archlinux
- [ ] Windows?

## Development

1. Follow the [official steps](https://github.com/therecipe/qt/wiki/Installation) to set up a Go project in **Module Mode**.
2. Test app using `$ qtdeploy -debug -uic=false -quickcompiler test`
3. Package for deployment `$ qtdeploy -uic=false -quickcompiler build`

Important folders:

- `/ui` has `.ui` files provided by Qt Designer
- `/qml` has icons and other assets


## Deployment

See the `Makefile` for different deployment options. Needs Docker installed. E.g.

- `$ make darwin`
- `$ make linux DISTRO=archlinux`

For Linux, Qt5 is linked dynamically to match your distro's look and feel. Install required Qt5 packages like this:

- Ubuntu/Debian: `$ apt install qt5-default libqt5qml5`
- Archlinux: `$ pacman -S qt5`
- Fedora: `$ yum install qt5-qtbase`

## Translations
- extract strings: `lupdate -extensions ui ui/*.ui -ts qml/i18n/ui_en.ts`
- merge .ts files: `lconvert -i primary.ts secondary.ts -o complete.ts` 
- compile .ts to .qm: `lrelease qml/i18n/ui_de.ts -qm qml/i18n/ui_de.qm`

## License and Credits
- Thank you to all the people who already contributed to Vorta: [code](https://github.com/borgbase/vorta/graphs/contributors), [translations](https://github.com/borgbase/vorta/issues/159)
- Licensed under GPLv3. See [LICENSE.txt](LICENSE.txt) for details.
- Icons by [FontAwesome](https://fontawesome.com)
