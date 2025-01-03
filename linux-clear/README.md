# linux-clear
This repository contains the `PKGBUILD` file required for building the `linux-clear` and `linux-clear-headers` packages.
You can find this package [on the AUR](https://aur.archlinux.org/pkgbase/linux-clear).

## How to build and install
[Read this Arch Linux Wiki article.](https://wiki.archlinux.org/title/Arch_User_Repository)

## Updates
This package is usually updated 0-3 days after a kernel release.
If a security-relevant update is available the package will be updated as soon as possible.

## Environment variables
The PKGBUILD file supports customization via environment variables. Here's a list of all of them:
- `_makemenuconfig`: Invokes `make menuconfig` (ncurses-based default configuration menu) before compilation starts
- `_makenconfig`: Invokes `make nconfig` (ncurses-based nicer configuration menu) before compilation starts
- `_makexconfig`: Invokes `make xconfig` (X11-based GUI configuration menu) before compilation starts
- `_reuse_current`: Will use the configuration of the running kernel, if the running kernel is compiled with `IKCONFIG_PROC`
- `_reuse_file`: Will use the configuration file named `kconfig` contained in the `PKGBUILD` file's directory
- `_update_kconfig_on_reuse`: Specifies whether the kernel configuration shall be updated when using any of the '_reuse_*' flags
- `_copyfinalconfig`: Copies the final kernel configuration into the repository root as `kconfig-new` before compilation starts
- `_localmodcfg`: Only compiles modules found in modprobed-db's database (which decreases compilation time and kernel size)
- `_use_llvm_lto`: Compiles the kernel with LLVM instead of GCC. Should work, if not open an issue
- `_subarch`: Specifies the subarchitecture to compile for (see the [`PKGBUILD` file](https://git.staropensource.de/JeremyStarTM/aur-linux-clear/src/branch/develop/PKGBUILD) for a list of all subarches). Default is `41` (Generic x86-64), which is compatible with all amd64 processors. Must be a number
- `_use_llvm_lto`: Enables compilation with LLVM. Untested but should work. If not write a comment on the AUR.
- `_subarch_microarch`: Specifies the microarchitecture to compile for. Only applies to and is required by the `GENERIC_CPU` subarch. Must be a number between `1` and `4` ([click for more information](https://en.wikipedia.org/wiki/X86-64#Microarchitecture_levels))
- `_debug_kernel`: Force enables kernel debugging options when set to `y`, force disables debug options when set to `n` or relies on the kconfig when unset
- `_debug_script`: Enables debugging for the `PKGBUILD` file

All of these variables just need to be set for them to apply, except for `_subarch`, `_subarch_microarch` and `_debug_kernel`. **For more information please check their documentation inside the `PKGBUILD` file**

## GPG errors
If makepkg complains about invalid PGP keys, try running this command:
```bash
gpg --locate-keys torvalds@kernel.org gregkh@kernel.org sashal@kernel.org benhh@debian.org
```
This command only needs to be executed once.

## Issue handling
Please only submit issues if they aren't bug reports about the package or help requests.
Please keep them on the AUR only. This prevents unnecessary signups.

## Branches
This repository (at least if you view it on [sos!git](https://git.staropensource.de/JeremyStarTM/aur-linux-clear))
has two branches: `master` and `develop`. The `master` branch is the stable branch, where stable changes
are introduced. The `develop` branch is (as you might have already guessed) the development branch.

Please only submit PRs to the `develop` branch. Pull requests to the `master` branch will be rejected.

## License
This package does not yet have a license as the original repository (before [me](https://git.staropensource.de/JeremyStarTM) becoming it's maintainer) did not have one yet.
I have contacted [metak](https://aur.archlinux.org/account/metak) (the previous maintainer) to negotiate a license.

## Build tool
*If you want a dead simple way to compile this package, you can [try out my build tool](https://git.staropensource.de/JeremyStarTM/jstm-optimized). It includes a few no nonsense changes to the kernel configuration and allows you to configure the PKGBUILD in a simple manner to decrease build time. If you don't want that, using `makepkg` as-is works fine too.*
