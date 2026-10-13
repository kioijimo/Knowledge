
##### 04-10-2026
**Goal**: To fix a glaring issue of kernel `linux-cachyos-bore-lto` preset not present with `mkinitcpio`

**What happened:**
After uninstalling the standard kernel (linux-cachyos and linux-cachyos-lts), I installed the bore-lto version. Whilst trying to rebuild the kernel with `mkinitcpio` hook from `limine`, it fails during the compression part and skips the process. 

**Found issue:**
There’s no preset of the kernel available in the `/etc/mkinitcpio.d/` directory which the tool uses to rebuild the kernel.

**Fix:**
By running `mkinitcpio -p linux-cachyos-bore-lto`, it specified which kernel to rebuild and detects that there’s no preset available which prompts the user to create one and proceed. Afterwards, the kernel is rebuilt naturally. 

**Learnings:**
`mkinitcpio` is a type of automatic rebuilding tool for the kernel like `dracut`. CachyOS is an Arch derivative and such, comes built-in with `mkinitcpio`. [^1]While `dracut` is being considered as replacement and [^2]users are aiming to move to it, I don’t have the required knowledge and understanding to consider doing so yet.


[^1]:  Razzolini, Giancarlo. “Mkinitcpio Replacement with Dracut.” _Arch-Dev-Republic_. Pipermail, February 19, 2019. https://lists.archlinux.org/pipermail/arch-dev-public/2021-February/030344.html.

[^2]: “Move to Dracut (Leaving Mkinitcpio).” Web log. _KaOS Forums_ (blog). KaOS, March 31, 2021. https://forum.kaosx.us/d/2791-move-to-dracut-leaving-mkinitcpio.
