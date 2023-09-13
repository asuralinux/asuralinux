# Background

Linux is arguably the most widely deployed operating system in the world. While Linux has historically been a Unix-like operating system, it should be fair to say a modern Linux distribution is much more than a behavior aggregation of the fifty-year-old Unix legacy.

While there is a lot to be excited about the current state of Linux distributions, if you look closely enough, you might see another new common thread emerging. Several major Linux projects are already experimenting with or considering "immutable" versions of their distributions.

These explorations are driven by the possibility of simplifying the user experience enabled by emerging technologies. While not all such projects share identical goals or approaches, there are common themes.

- Immutable / Reproducible system installations
- Atomic updates (w/ rollback) / Multi-root switching file systems
- Application channel diversity

Some examples for such Linux distributions are as follows.

- Fedora [Silverblue](https://fedoraproject.org/silverblue/) / [Kinoite](https://fedoraproject.org/kinoite/) / [Sericea](https://fedoraproject.org/sericea/)
- openSUSE [Aeon](https://en.opensuse.org/Portal:Aeon) / [Kalpa](https://en.opensuse.org/Portal:Kalpa)
- [NixOS](https://nixos.org/)
- [Flatcar Container Linux](https://www.flatcar.org/)
- [Vanilla OS](https://vanillaos.org/)

If we consider the above themes as design goals, we can see more distros falling into the same group. For example [GNOME OS](https://os.gnome.org/) (not intended for end users), [Clear Linux](https://clearlinux.org/), [Endless OS](https://www.endlessos.org/), [carbonOS](https://carbon.sh/), [blendOS](https://blendos.co/), [Liri](https://liri.io/), [LinuxKit](https://github.com/linuxkit/linuxkit), [Talos Linux](https://www.talos.dev/), [Ubuntu Core Desktop](https://ubuntu.com/blog/ubuntu-core-an-immutable-linux-desktop), [rlxos](https://rlxos.dev/), [astOS](https://github.com/CuBeRJAN/astOS), [AshOS](https://github.com/ashos/ashos), [Kairos](https://kairos.io/), and [Universal Blue](https://universal-blue.org/) (variants) share one or more characteristics above.

Even with common desired characteristics, how each project interprets them can differ. For example,
- While Fedora Silverblue uses libostree to achieve immutability and multi-root, openSUSE Aeon uses btrfs snapshots towards the same goal. They both result in an immutable Linux OS with GNOME Desktop Environment (DE) by traveling different paths. NixOS can also arrive at roughly the same destination by being reproducible (as opposed to immutable). For some other distros, immutability might be merely an emergent property rather than a design goal.
- While Vanilla OS uses ABRoot to gain dual roots for pre and post-update states, Silverblue uses libostree to gain multiple file system roots, which can be more than two.
- NixOS uses the Nix packaging system enabled by its active user community to maintain a historical repository containing every known version of available software. On the other hand, Flatcar optimizes only running OCI containers in a server setting, whereas Vanilla OS enables the user to install software from Flatpak, multiple package management systems, and OCI containers in a desktop setting.

Fortunately, there are recent efforts to find common ground to collaborate and define specifications around shared interests. A prominent such collaboration is [the Linux Userspace API (UAPI) Group](https://uapi-group.org/). They are developing consensus among people building immutable, image-based, managed, measured-boot, secure-boot, etc. Linux systems. Unfortunately, there is still no universally accepted umbrella term to call these. In this document, we may call them image-based, immutable, or managed Linux interchangeably, interpreting them as generic terms (unless specified).

An immutable Linux system should make the user's life easier, in theory. However, the current reality is far from it. They deviate from traditional workflows but do not have sufficient support information. More importantly, customization requires significant technical skills to achieve the desired results.
