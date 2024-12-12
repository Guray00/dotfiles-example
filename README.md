dotfiles
========

This repo is an example of how to manage dotfiles with Ansible. The main goal is to have a simple and easy way to manage dotfiles and configurations across multiple machines, without making it too much complex.

### Installation

0. Install Xcode Command Line Tools:

    ```bash
    xcode-select --install
    sudo xcodebuild -license accept
    ```

1. Make sure to uprade Pip Homebrew before installing Ansible:

    ```bash
    sudo pip3 install --upgrade pip
    pip3 install ansible
    ```

2. Fork this repository:

    ```bash
    git clone https://github.com/guray00/dotfiles-example ~/.dotfiles
    ```

3. Copy and adjust the default configuration file:

    ```bash
    cp ~/.dotfiles/config.defaults.yml ~/.dotfiles/config.yml
    vi ~/.dotfiles/config.yml
    ```

4. Run the dotfile wrapper with the `--bootstrap` switch to initially install and setup the dotfiles and its components:

    ```bash
    ~/.dotfiles/dotfiles --bootstrap
    ```

### Available commands

```bash
# (Re-)apply dotfile related tasks
$ dotfiles

# (Re-)apply dotfile and bootstrap related tasks (by default only "dotfiles" will be execated when not specifying --botstrap)
$ dotfiles --bootstrap

# Apply a specific tag/task
$ dotfiles <tag>
```

### Information

Explanation of the directories:

```
./files/
└── This directory contains all optional files that are not related to
    Ansible roles in specific. For example: dotfile source files, iTerm
    configuration files, etc.

./files/dotfiles/
└── This folder contains all the source dotfiles.

./files/iterm2/
└── This folder contains the iTerm 2 plist configuration.

./roles/
└── In this directory you will find all available Ansible roles that I
    currently use within this project.

./roles/{rolename}/tasks/main.yml
└── This is the actual Ansible tasks that uses the variable (defaults)
    file and proceeds with the role specific function.

./ansible.cfg
└── Ansible configuration file that is applied when executing the
    dotfile wrapper / playbook.

./config.defaults.yml
└── This file contains variables to work with in the actual Ansible
    tasks like package names/lists, configuration options, etc.

./config.yml
└── This (optional) file can be used to override the defaults (above)
    as as desired, not tracked by git.

./dotfiles
└── Basically the base wrapper that I use to install and update the
    dotfiles as well as interact with the `ansible-playbook` command.

./dotfiles.yml
└── The main Ansible playbook.

./hosts
└── The inventory file for Ansible, for now it only contains the
    localhost machine

./requirements.yml
└── Ansible role and collection dependencies which are somehow in use by
    this playbook.
```

### License

[MIT](LICENSE)

### Version

2.0

## Reference

This configuration is a fork of https://github.com/frdmn/dotfiles