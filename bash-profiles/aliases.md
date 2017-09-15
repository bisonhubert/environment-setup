# Bash Aliases

## Git
alias ga='git add'  
alias gc='git commit -v'  
alias gcam='git commit -a -m'  
alias gcsm='git commit -s -m'  
alias gob='git checkout -b'  
alias gcf='git config --list'  
alias gcl='git clone --recursive'  
alias gclean='git clean -fd'  
alias gpristine='git reset --hard && git clean -dfx'  
alias gom='git checkout master'  
alias god='git checkout develop'  
alias gcmsg='git commit -m'  
alias go='git checkout'  
alias gcount='git shortlog -sn'  
alias grt='cd $(git rev-parse --show-toplevel || echo ".")'  
alias gsb='git status -sb'  