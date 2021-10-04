# Dotfiles repo

Personal dotfiles repo

With this repo I followed this [guide](https://dev.to/jakewies/manage-your-dotfiles-like-a-superhero-4gpd) to store my dotfiles



### Quick steps

1. Clone this repo into your home folder, creating a ".dotfiles" directory

2. Install "stow" package

   ```bash
   sudo apt install stow
   ```

   

3. Launch stow command for each package's config you want import

   ```bash
   stow git
   stow vim
   stow ssh
   ```

   

### Stow basics

Tree structure

```
target-directory (your home directory)
├── stow-directory (cloned repo, '.dotfiles' directory)
│   ├── package-1 (package folder)
│   │   └── .dotfile-1 (package's config file)
│   ├── package-2
│   │   └── .dotfile-2
│       └── .dotfile-3
```



Stow utility will symlink the contents of each package to the target directory.



#### Example n.1

Starting tree

```
/Users/youruser
├── .dotfiles
│   ├── vim
│   │   └── .vimrc
```



After launching stow command (`stow vim`)

```
/Users/youruser
├── .dotfiles
│   ├── vim
│   │   └── .vimrc
├── .vimrc -> .dotfiles/vim/.vimrc
```



#### Example n.2

Starting tree (with single packages using a subfolder to store their dotfiles)

```
/Users/youruser
├── .dotfiles
│   ├── vim
│       └── .vimrc
│       └── .vim
|           └── script.vim
```



After launching stow command (`stow vim`)

```
/Users/youruser
├── .dotfiles
│   ├── vim
│       └── .vimrc
│       └── .vim
|           └── script.vim
├── .vimrc -> .dotfiles/vim/.vimrc
├── .vim   -> .dotfiles/vim/.vim
|   └── script.vim
```