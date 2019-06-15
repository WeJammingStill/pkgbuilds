all:
	@echo "Run 'make install' to install."
	@echo "Run 'make locale' to install timezone configuration."
	@echo "Run 'make fonts' to install font configuration."
	@echo "Run 'make mouse_keyboard' to install mouse & keyboard configuration."
	@echo "Run 'make neovim' to install neovim/vim/vi symlink."
	@echo "Run 'make uninstall' to uninstall all configurations."
install:
	@echo "Installing font configuration."
	@mkdir -p /etc/fonts/
	@install -Dm 0644 fontconfig-local.conf /etc/fonts/local.conf
	@install -Dm 0644 69-emoji.conf /etc/fonts/conf.d/69-emoji.conf
	@install -Dm 0644 70-no-dejavu.conf /etc/fonts/conf.d/70-no-dejavu.conf
	@echo "Installing repos configuration."
	@mkdir -p /etc/pacman.d/
	@install -Dm 0644 unofficial-repos /etc/pacman.d/unofficial
	@echo "Include = /etc/pacman.d/unofficial" >> /etc/pacman.conf
	@install -Dm 0644 pkglist.hook /usr/share/libalpm/hooks/pkglist.hook
	@echo "Installing mouse and keyboard configuration."
	@mkdir -p /etc/xorg.conf.d/
	@install -Dm 0644 00-keyboard.conf /etc/X11/xorg.conf.d/00-keyboard.conf
	@install -Dm 0644 30-touchpad.conf /etc/X11/xorg.conf.d/30-touchpad.conf
	@echo "Installing neovim symlinks."
	@ln -sf /usr/bin/nvim /usr/bin/vi
	@ln -sf /usr/bin/nvim /usr/bin/vim
	@echo "Installing timezone configuration."
	@systemctl enable --now systemd-timesyncd
	@ln -sf /usr/share/zoneinfo/Asia/Taipei /etc/localtime
	@sed 's/#en_US/en_US/' -i /etc/locale.gen
	@sed 's/#zh_TW/en_US/' -i /etc/locale.gen
	@locale-gen

locale:
	@echo "Installing timezone configuration."
	@systemctl enable --now systemd-timesyncd
	@ln -sf /usr/share/zoneinfo/Asia/Taipei /etc/localtime
	@sed 's/#en_US/en_US/' -i /etc/locale.gen
	@sed 's/#zh_TW/en_US/' -i /etc/locale.gen
	@locale-gen

neovim:
	@echo "Installing neovim symlinks."
	@ln -sf /usr/bin/nvim /usr/bin/vi
	@ln -sf /usr/bin/nvim /usr/bin/vim

fonts:
	@echo "Installing font configuration."
	@mkdir -p /etc/fonts/
	@install -Dm 0644 fontconfig-local.conf /etc/fonts/local.conf
	@install -Dm 0644 69-emoji.conf /etc/fonts/conf.d/69-emoji.conf
	@install -Dm 0644 70-no-dejavu.conf /etc/fonts/conf.d/70-no-dejavu.conf

repos:
	@echo "Installing repos configuration."
	@mkdir -p /etc/pacman.d/
	@install -Dm 0644 unofficial-repos /etc/pacman.d/unofficial
	@echo "Include = /etc/pacman.d/unofficial" >> /etc/pacman.conf
	@install -Dm 0644 pkglist.hook /usr/share/libalpm/hooks/pkglist.hook

mouse_keyboard:
	@echo "Installing mouse and keyboard configuration."
	@mkdir -p /etc/xorg.conf.d/
	@install -Dm 0644 00-keyboard.conf /etc/X11/xorg.conf.d/00-keyboard.conf
	@install -Dm 0644 30-touchpad.conf /etc/X11/xorg.conf.d/30-touchpad.conf

uninstall:
	@rm -fr /etc/fonts/local.conf
	@rm -fr /etc/fonts/conf.d/69-emoji.conf
	@rm -fr /etc/fonts/conf.d/70-no-dejavu.conf
	@rm -fr /etc/pacman.d/unoffical
	@rm -fr /usr/share/libalpm/hooks/pkglist.hook
	@rm -fr /etc/X11/xorg.conf.d/00-keyboard.conf
	@rm -fr /etc/X11/xorg.conf.d/30-touchpad.conf
