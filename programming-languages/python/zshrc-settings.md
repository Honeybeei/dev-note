# ⚙️ My zshrc-settings

- [⚙️ My zshrc-settings](#️-my-zshrc-settings)
  - [🔑 Key Words](#-key-words)
  - [👀 Fast Lookup](#-fast-lookup)
  - [📜 `.zshrc`](#-zshrc)

## 🔑 Key Words

- zshrc

## 👀 Fast Lookup

This is just a collection of my zshrc settings for Python development.

## 📜 `.zshrc` 

```zsh
# python.zsh. It will be sourced in .zshrc

#####################################
# function for creating python venv #
#####################################
create_venv() {
  # check if .venv exists
  if [ -d ".venv" ]; then
    echo $(color_string $kRed "Error: .venv already exists. Please deactivate it first.")
    return 1
  fi

  # Get Global Python Version
  global_python_version=$(python --version | cut -d " " -f 2 | cut -d "." -f 1,2)
  echo "Global Python Version: $(color_string $kGreen $global_python_version)"

  # prompt user for python version
  echo "Enter the python version (e.g. 3.11 | default: $(color_string $kGreen $global_python_version)):"
  read -r python_version
  # if the user does not provide python version, use the global python version
  if [ -z "$python_version" ]; then
    python_version=$global_python_version
  fi

  # create venv
  python$python_version -m venv .venv
  echo "Virtual environment created [$(color_string $kGreen $python_version)]"

  source .venv/bin/activate
  venv_version=$(python --version)
  echo "Virtual environment activated [$(color_string $kGreen $venv_version)]"
  # ask user to add .venv to .gitignore
  echo "Do you want to add .venv to .gitignore? (y/n)"
  read -r confirmation
  if [[ $confirmation == "y" ]]; then
    echo ".venv" >>.gitignore
    echo ".venv added to .gitignore"
  fi
}

#####################################
# function for activating python venv
#####################################
activate_python_venv() {
  # check if venv already activated
  if [ -n "$VIRTUAL_ENV" ]; then
    echo "$(color_string $kRed "Error: Virtual environment is already activated.")"
    return 1
  fi
  # check if .venv exists
  if [ ! -d ".venv" ]; then
    echo "$(color_string $kRed "Error: .venv does not exist. Please create it first.")"
    return 1
  fi
  source .venv/bin/activate
  venv_version=$(python --version)
  echo "Virtual environment activated!: [$(color_string $kGreen $venv_version)]"
  echo "Activated interpreter         : $(color_string $kGreen "$(which python3)")"
}

###################################################
# function for adding dependencies to python venv #
###################################################
add_dependency() {
  if [ $# -eq 0 ]; then
    echo "Error: Please provide a dependency name."
    return 1
  fi

  # add all dependencies and freeze
  pip install $*
  pip freeze > requirements.txt
  echo "Dependency added: $*"
}

#######################################################
# function for delete all poetry virtual environments #
#######################################################
delete_all_poetry_virtual_environments() {
  echo "Deleting all poetry virtual environments..."
  rm -rf $HOME/Library/Caches/pypoetry/virtualenvs/*
  echo "All poetry virtual environments deleted."
}

###########################################
# function for creating package directory #
###########################################
create_package() {
  # ask user for the name of the new directory
  echo "Enter the name of the new directory:"
  read -r package_name
  if [ -z "$package_name" ]; then
    echo "$(color_string $kRed "Error: Package name cannot be empty.")"
    return 1
  fi
  mkdir $package_name
  touch $package_name/__init__.py

  echo "Package created: $(color_string $kGreen $package_name)"
}

############################################
# function for creating flake8 config file #
############################################
create_flake8_config() {
  touch .flake8
  echo "[flake8]" >>.flake8
  echo "max-line-length = 120" >>.flake8
  echo "ignore = E203 # whitespace before ':'" >>.flake8
  echo "ignore = E266 # too many leading '#' for block comment" >>.flake8
  echo "ignore = E501 # line too long (82 > 79 characters)" >>.flake8
  echo "exclude = .git,__pycache__,.venv" >>.flake8
}

###########
# aliases #
###########
alias python="python3"
alias pip="pip3"
alias py="python3"
alias py-venv-create="create_venv"
alias py-venv-activate="activate_python_venv"
alias py-venv-deactivate="deactivate"
alias py-venv-freeze="pip freeze > requirements.txt"
alias py-venv-install="pip install -r requirements.txt"
alias py-venv-add="add_dependency"
alias py-create-package="create_package"
alias py-create-flake8-config="create_flake8_config"
alias py-poetry-clean="delete_all_poetry_virtual_environments"
```

[🔙 Back to the main page]( README)
