#ZSHRC
##Add below settings
```
unalias run-help
autoload run-help
HELPDIR=/usr/local/share/zsh/help


# zsh completion
fpath=(/usr/local/share/zsh-completions $fpath)
fpath=(/usr/local/share/zsh/site-functions $fpath)
fpath=(/usr/local/share/zsh/functions $fpath)
fpath=(~/.zsh/completion $fpath)

autoload -Uz compinit && compinit -i

# alias
alias ..="cd .."
alias ...="cd ../.."
alias ....="cd ../../.."
alias .....="cd ../../../.."

alias du='du -h -d 1'
alias htop='sudo htop'
alias icloud="brctl log --wait --shorten"
alias ip="ipconfig getifaddr en0"

# home/bin
export PATH=$HOME/bin:$PATH

# rbenv
export RBENV_ROOT=/usr/local/var/rbenv
if which rbenv > /dev/null; then eval "$(rbenv init -)"; fi

# pyenv
export PYENV_ROOT=/usr/local/var/pyenv
if which pyenv > /dev/null; then eval "$(pyenv init -)"; fi

# jenv
export JENV_ROOT=/usr/local/opt/jenv
if which jenv > /dev/null; then eval "$(jenv init -)"; fi

# less highlight
export LESSOPEN="| src-hilite-lesspipe.sh %s"
export LESS=" -R "

# groovy
export GROOVY_HOME=/usr/local/opt/groovy/libexec

# maven
export MAVEN_OPTS="$MAVEN_OPTS -XX:+TieredCompilation -XX:TieredStopAtLevel=1"

# nvm
export NVM_DIR=~/.nvm
source $(brew --prefix nvm)/nvm.sh

# android
export ANDROID_HOME=/usr/local/opt/android-sdk

# go
export GOROOT=/usr/local/opt/go/libexec
export GOPATH=/Users/bananayong/gocode
export PATH=$PATH:$GOROOT/bin:$GOPATH/bin

# z
source `brew --prefix`/etc/profile.d/z.sh

# history
HISTSIZE=50000
SAVEHIST=50000

# ulimit
ulimit -n 4096

# LANG
export LANG=ko_KR.UTF-8

# iterm
test -e "${HOME}/.iterm2_shell_integration.zsh" && source "${HOME}/.iterm2_shell_integration.zsh"

# fortune & cowsay
modular=$(cowsay -l | tail -n +2 | tr ' ' '\n' | wc -l)
timestamp=$(date +"%s")
let "select = $timestamp % $modular + 1"
animal=$(cowsay -l | tail -n +2 | tr ' ' '\n' | sed "${select}q;d")

fortune | cowsay -f $animal | lolcat
```
