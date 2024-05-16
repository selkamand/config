## Config

This repo seeks to speed up setup time on new devices by consolidating 
configuration files for applications like tmux, rstudio, fish, etc all in the one place


## Instructions

### Setup Terminal

End goal is a terminal that looks roughly like this:

![alt text](images/image-3.png)

1. Install [Alacritty](https://github.com/alacritty/alacritty?tab=readme-ov-file). Mac default terminal isn't bad either.
2. (on mac) Install [homebrew](https://brew.sh/)
3. `brew install fish` and set to default shell.
4. Set default shell (`echo /opt/homebrew/bin/fish | sudo tee -a /etc/shells; chsh -s /opt/homebrew/bin/fish`)
6. Install [fisher](https://github.com/jorgebucaran/fisher) for fish plugin management
7. Install [tide](https://github.com/IlanCosman/tide) for a prettier prompt (don't forget to install the Nerd fonts as described on the bottom of the github readme)

#### Terminal Multiplexing (TMUX)
6. Install tmux for terminal multiplexing (`brew install tmux`)
7. Copy `config/.tmux.conf` to `~/.tmux.conf`
8. `Ctrl-b + r` to reload tmux conf then `Ctrl-b + I` to install plugins


### Core Scripts

I usually like having a folder of quick scripts added to my path
```
#Add custom path to path
set PATH {$PATH}:"/Path/To/custom_scripts"
```

For scripts to add see: 
[assorted_bash_utils](https://github.com/selkamand/assorted_bash_utils)


### Aliases

On linux, to replicate pbcopy/pbaste commands use the following aliases
```
alias pbcopy 'xclip -selection clipboard'
alias pbpaste 'xclip -selection clipboard -o'
funcsave pbcopy
funcsave pbpaste
```

On most platforms, you'll need to make ls colourful
```
alias ls 'ls -G'
funcsave ls
```

and define ll (longlist) yourself
```
alias ll 'ls -lh'
funcsave ll
```


### Most important basic software installs

On mac
```
brew install \
# Utilities
aria2 \ # fast downloads
htop \ # better top


# Bioinformatics sofware
htslib \ 
samtools \
bcftools \

## Containerisation / Virtualisation
docker \
lazydocker \ # Terminal Interface for docker management

# Dependency Managers
micromamba \ # Complete conda rewrite in C++ for speed - no python dep :)

modules # environment-modules. might be worth trying Lmod instead which is newer
```

## Languages

### Java
1. Install [SDKman for fish](https://github.com/reitzig/sdkman-for-fish)
2. `sdk install java`

### R

1. Install [R and Rstudio](https://posit.co/download/rstudio-desktop/)
2. Copy `config/.Rprofile` to `~/.Rprofile` so new packages have the right author info. If you're not the owner of this repo, either skip this or change .Rprofile to your information)
3. In Rstudio, edit snippets - than replace all with content from `r.snippets`

Can use Rswitch to manage multiple R installs / renv for R package virtual environments.


### Rust
Install [rust](https://www.rust-lang.org/tools/install) 

### Python

My preferred way to manage python is [pyenv](https://github.com/pyenv/pyenv) (`brew install pyenv`)

## GUI software
* VScode for rust/python/js/bash dev.


### More software you can't install from brew

1. [Nextflow](https://www.nextflow.io/docs/latest/install.html)
