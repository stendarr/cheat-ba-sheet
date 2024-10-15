# cheat ba sheet
my personal cheat sheet for bash and related stuff

notice the lack of capitalization and punctuation? that's because it's all casual and not serious and stuff

## loops
### numerical
```
for ((i = 0 ; i < 5 ; i++ )); do echo "$i"; done
0
1
2
3
4
for ((i = 0 ; i < 5 ; i++ )); do mkdir "year-202$i"; done
```
### infinite
interruptible with ctrl+c
```
while :; do echo 'waiting'; sleep 1; done
```
`while :` is the same as `while true`
### over filenames
all files/directories in current directory, non-recursive, leaves hidden files (dotfiles) untouched
```
for filename in *; do mv "${filename}" "${filename}-backup"; done
```
bash does not match dotfiles when globbing with *, however, this can be set with `shopt -s dotglob` and unset with `shopt -u dotglob`

to only do it for a single command you could
```
shopt -s dotglob; for filename in *; do mv "${filename}" "${filename}-backup"; done; shopt -u dotglob
```
for zsh use `setopt`
```
setopt GLOB_DOTS; for filename in *; do mv "${filename}" "${filename}-backup"; done; unsetopt GLOB_DOTS
```
