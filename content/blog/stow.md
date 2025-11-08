+++
date = '2025-11-08T01:44:31Z'
title = 'Using GNU Stow for managing your dotfiles'
weight = '2'
+++
A few years back, I discovered a program called GNU Stow through a video on Wolfgang's Channel which is as defined by the man page:


> *"a symlink farm manager which takes distinct packages of software and/or data located in separate directories on the filesystem, and makes them appear to be installed in the same place."*

I found that it was very useful for managing your dotfiles and various configurations in a clean manner instead of having to manually symlink everything together, and today I will guide you on how to use it so you can worry about configuring neovim instead of worrying about if your dotfiles are symlinked or not ;)

To begin, install stow using your distributions package manager

```
sudo pacman -S stow
```

Then create a dotfiles folder in your home directory and move all of your existing configurations there with a structure as follows
```
.
├── dunst
│   └── .config
│       └── dunst
│           └── dunstrc
├── fastfetch
│   └── .config
│       └── fastfetch
│           └── config.jsonc
├── ok.txt
├── picom
│   └── .config
│       └── picom
│           ├── picom.conf
│           └── picom.conf.save
├── rofi
│   └── .config
│       └── rofi
│           ├── config
│           └── themes
│               └── merah.rasi
├── tmux
│   ├── .tmux
│   │   └── plugins
│   │       ├── tmux-sensible
│   │       └── tpm
│   └── .tmux.conf
├── xorg
│   ├── .xinitrc
│   ├── .Xprofile
│   └── .Xresources
└── zsh
    └── .zshrc
```

Once done, make sure all of your configs are removed from the .config directory in your home directory and then move into your dotfiles folder and run the following command to deploy your dotfiles:

```
stow *
```

Or if you wish to only deploy certain specified folders run:

```
stow rofi picom xorg fastfetch
```

And that's it, its as simple as that, now all of your dotfiles will automatically be symlinked and you can now initalise a git repo inside of the newly created dotfiles folder for easy version control, happy ricing :)
