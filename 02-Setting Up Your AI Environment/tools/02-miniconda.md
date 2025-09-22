<img src="https://www.anaconda.com/wp-content/uploads/2024/11/2020_Anaconda_Logo_RGB_Corporate.png" width="150"> 
3. Python Environment Manager ( VENV, Mini Conda )
Downlaod and install Miniconda

- Link to Download:[Miniconda ](https://www.anaconda.com/docs/getting-started/miniconda/install#using-miniconda-in-a-commercial-setting)
```
# mac-intel last version support
curl -O https://repo.anaconda.com/miniconda/Miniconda3-py39_25.7.0-2-MacOSX-x86_64.sh

# mac-arm 
curl -Ohttps://repo.anaconda.com/miniconda/Miniconda3-latest-MacOSX-arm64.sh

# bash ~/Miniconda3-py39_25.7.0-2-MacOSX-x86_64.sh
```
---
FIX problem 

edit file ~/.zshrc
remove or command 
```
# >>> conda initialize >>>
# !! Contents within this block are managed by 'conda init' !!


#__conda_setup="$('/Users/thanit/miniconda3/bin/conda' 'shell.zsh' 'hook' 2> /dev/null)"
#if [ $? -eq 0 ]; then
#    eval "$__conda_setup"
#else
#    if [ -f "/Users/thanit/miniconda3/etc/profile.d/conda.sh" ]; then
#        . "/Users/thanit/miniconda3/etc/profile.d/conda.sh"
#    else
#        export PATH="/Users/thanit/miniconda3/bin:$PATH"
#    fi
#fi
#unset __conda_setup

# <<< conda initialize <<<

```
add this two line:
```
export PATH="/Users/thanit/miniconda3/bin:$PATH"
alias conda-init='source ~/miniconda3/etc/profile.d/conda.sh'
```

When ever need to ACTIVE CONDA use this command 
```
conda-init
conda actviate base  // or you environment anme
```


