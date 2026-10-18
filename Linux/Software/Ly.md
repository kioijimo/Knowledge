##### 04-11-2026
**Goal:** To install and customize **ly (display manager)**

**Steps:**
To use the display manager, first is to install it through your package manager. On Arch and arch-based distros, it’s `sudo pacman -S ly`  or with your preferred AUR helper (`yay -S ly`).

After installing, enable the ly service. To enable it, use `sudo systemctl enable ly@tty2.service` and  find `autovt@.service`  in your `/etc/systemd/system/multi-user.target.wants` directory and disable it with `sudo systemctl disable autovt@.service`. This will disable the service it a symlink of which is `getty@.service` under the `usr/lib/systemd/system` directory[^1].

This process basically replaces the virtual terminal ly uses from `agetty` to `ly`. Note that this only replaces the `tty2` as per ly’s service indicates. I don’t know why attempting to disable all the `autovt@X.service` does not close off the default 6 VTs of Arch, but moving forward.

**Customizing:**
Now that ly has been enabled as the starting VT, you can configure it through `/etc/ly/config.ini`. The `config.ini` itself is pretty documented so you won’t get lost in configuring it. 

**Challenges:**
Colors are in the hexadecimal format so convert your colors to it before putting it in otherwise it wouldn’t work. For the `asterisk` config which supposedly supports UTF-8 characters, I have noticed some of the characters are not working properly so be mindful of that as well. The configuration, mainly the colors, break when `asterisk` is incompatible with the valid UTF-8 characters. Even after all that, the colors are not entirely correct, mainly the background and foreground of the display. 

**Fix:**
As of now, the terminal colors, primarily the background and foreground, are not working properly and require additional setup. To fix this, you have to edit `ly@.service` under `/lib/systemd/system` directory and add a `ExecStartPre` config. Set `/usr/bin/printf '%%bb' '\e]P0{your-bg}\e]PF{your-fg}\ec'` as its value. This tells the ly service to use printf and use the set colors before executing ly itself[^2]. 

[^1]: "GitHub - Fairyglade/ly: A Lightweight TUI (Ncurses-Like) Display Manager for Linux and BSD (Mirror of Https://codeberg.org/fairyglade/ly)." GitHub. https://github.com/fairyglade/ly.

[^2]: Guide: How to Change the Colors of Ly (Display Manager)." Gist. https://gist.github.com/jessedavidd/dd3b3a6a4b922d611006d194e82e7103?permalink_comment_id=5382644.
