# Beautify your Terminal
Below Steps will help to modify and beautify the terminal so that work becomes easy by using zsh, oh-my-zsh, syntax highlighting, auto completion, kubectx, Kubecolor 

# 1. Install zsh on Ubuntu Box
Open ubuntu Terminal and run the below comamnds:  

    sudo apt-get update
    sudo apt-get install zsh
    zsh --version


# 2. Install oh-my-zsh-in-ubuntu
Open ubuntu Terminal and run the below comamnds:  

    sudo apt install curl wget git
    sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
    OR
    sh -c "$(wget https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh -O -)"

OH-MY-ZSH Plugins:  

    git clone https://github.com/zsh-users/zsh-autosuggestions.git $ZSH_CUSTOM/plugins/zsh-autosuggestions
    git clone https://github.com/zsh-users/zsh-syntax-highlighting.git $ZSH_CUSTOM/plugins/zsh-syntax-highlighting
    nano ~/.zshrc
    plugins=(git zsh-autosuggestions zsh-syntax-highlighting)
    source ~/.zshrc

# 3. Customize your zsh 
Install PowerLevel9k!:

    git clone https://github.com/bhilburn/powerlevel9k.git ~/.oh-my-zsh/custom/themes/powerlevel9k
    nano ~/.zshrc

    And change and put these lines :

    ZSH_THEME="powerlevel9k/powerlevel9k"
    POWERLEVEL9K_DISABLE_RPROMPT=true
    POWERLEVEL9K_PROMPT_ON_NEWLINE=true
    POWERLEVEL9K_MULTILINE_LAST_PROMPT_PREFIX="▶"
    POWERLEVEL9K_MULTILINE_FIRST_PROMPT_PREFIX=""

# 4. Fonts and colors
In order to display all characters of the default prompt correctly, the shell should support UTF-8 and Nerd fonts (or at least the DejaVuSansMono Nerd font) should be installed. 

On Linux, you can install it like this:

    mkdir ~/.fonts
    curl -L -o ~/.fonts/DejaVuSansMonoNerdFontCompleteMono.ttf https://github.com/ryanoasis/nerd-fonts/raw/master/patched-fonts/DejaVuSansMono/Regular/complete/DejaVu%20Sans%20Mono%20Nerd%20Font%20Complete%20Mono.ttf
    fc-cache

On Windows, it can be installed via choco: (Choose this option if you have ubuntu app installed on windows machine)  

    choco install font-nerd-DejaVuSansMono

# 5. Redirect Brew to zsh binary file

    nano ~/.zshrc
    Add the below line at the end and save it
    eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)"

# 6. Kubectx
What are kubectx and kubens ?
kubectx is a tool to switch between contexts (clusters) on kubectl faster.
kubens is a tool to switch between Kubernetes namespaces (and configure them for kubectl) easily

Reference Documenation: https://github.com/ahmetb/kubectx  
If you use Homebrew you can install like this:  

    brew install kubectx

# 7. Kubecolor
Colorize your kubectl output
Reference Documenation: https://github.com/hidetatz/kubecolor  
If you use Homebrew you can install like this:  

    brew install hidetatz/tap/kubecolor

# 8. Use Few Alias in your .zshrc file to make your life easy:
    nano ~/.zshrc
    Add the below commands at the end:
    alias kgp="kubectl get pods"
    alias kga="kubectl get all"
    alias k="kubectl"
    alias hl="helm list"
    alias kubectl="kubecolor"
    alias ktx="kubectx"
    alias kns="kubens"
    alias mnt="/mnt/c/Users/Public/github"


