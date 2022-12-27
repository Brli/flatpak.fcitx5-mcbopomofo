Description
===

This repo contains flatpak script for [fcitx5-mcbopomofo](https://github.com/openvanilla/fcitx5-mcbopomofo) input method.

The main YAML is copied from M17n of [flatpak-fcitx5](https://github.com/fcitx/flatpak-fcitx5)
The fmt part is from [modules/fmt.yaml](https://github.com/fcitx/flatpak-fcitx5/tree/master/modules/fmt.yaml) of the same repo

Usage
===

1. Install tools: `flatpak`, `flatpak-builder`
    - follow the [Setup Guide](https://flatpak.org/setup/) from official page.

2. Build package

```bash
flatpak-builder --force-clean --install-deps-from=flathub --disable-cache --repo=/tmp/repo --user /tmp/app org.fcitx.Fcitx5.Addon.McBopomofo.yaml
---

--force-clean:      clean build directory if it is not empty.
--install-dep-from: install missing dependencies.
--disable-cache:    do not use ccache
--repo:             define repo directory, so you know where to export packages
--user:             use user repository, ensure operation runs without root privilege.
/tmp/app:           building directory.
```

3. Export single package for installation on other machine

```bash
flatpak build-bundle --runtime /tmp/repo Fcitx5-McBopomofo.flatpak org.fcitx.Fcitx5.Addon.McBopomofo stable
---

--runtime:                         the built package is a runtime.
/tmp/repo:                         the previous-defined repo directory.
Fcitx5-McBopomofo.flatpak:         the package name you choosed, with suffix.
org.fcitx.Fcitx5.Addon.McBopomofo: the application name in repo.
stable:                            the branch used in the yaml.
```

4. Move the exported `.flatpak` to target machine (ie. Steam Deck)

5. Install the .flatpak

```bash
flatpak install --user name.flatpak
```