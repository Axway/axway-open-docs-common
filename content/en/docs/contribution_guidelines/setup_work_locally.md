---
title: "Set up and work locally"
linkTitle: "Set up and work locally"
weight: 3
date: 2019-07-09
description: >
  How to set up and build this documentation site locally.
---

If you are a maintainer of this documentation site, or a contributor who will be making frequent or major contributions to the documentation, we recommend you set up and build the site locally on your computer. This enables you to easily test changes locally before pushing to GitHub.

## Set up environment and install required tools

Before you can build the site locally you must set up an environment and install the following tools.

* Git client - This is how you will interact with the GitHub repository.
* Hugo (extended version) - This is the static site generator that builds the HTML site from Markdown.
* Docsy - This is a documentation theme for Hugo.
* NodeJS - This is required by the Docsy theme to install the PostCSS dependencies using `npm`.

### Recommended environment

Although you can build the site on Windows or macOS, it is strongly recommended to use a Linux distribution, as this is what is used to build the production site on Netlify.

#### Windows Subsystem for Linux

If you are unfamiliar with Linux environments, you can get up and running very quickly by installing the [Windows Subsystem for Linux (WSL)](https://docs.microsoft.com/en-us/windows/wsl/about).

To install WSL on Windows 10, follow the [WSL installation guide on Microsoft Docs](https://docs.microsoft.com/en-us/windows/wsl/install-win10). This guide describes how to:

1. Enable the WSL feature in your Windows 10 installation.
2. Download and install a Linux distribution from the Microsoft Store. Select **Ubuntu 18.04 LTS**.
3. Initialize the Linux distro, including how to launch it for the first time, how to set up a Linux user account, and how to update and upgrade the packages in the distro.

It is important that you complete all of the steps in the WSL installation guide before proceeding.

{{% alert title="Tip" %}}
Learn how to configure your Ubuntu WSL shell in [Ubuntu tips](/docs/contribution_guidelines/setup_work_locally/#tips-for-configuring-ubuntu-wsl).
{{% /alert %}}

#### Gitbash on Windows

If for some reason you cannot use WSL or another Linux distribution, you can install and use [Gitbash for Windows](https://git-scm.com/download/win). In this case, you will need to use the Gitbash terminal to enter commands instead of the WSL terminal.

### Create a GitHub account and set up SSH keys

If you do not already have a GitHub account, go to [Sign up](https://github.com/join) to create one.

#### Generate SSH keys

Launch WSL and generate a new SSH key pair:

```
ssh-keygen -t ed25519
```

Press Enter when prompted for a path and a passphrase. You can find more detailed information in [Generating a new SSH key pair](https://docs.gitlab.com/ee/ssh/#generating-a-new-ssh-key-pair).

#### Add SSH key to your GitHub account

1. On GitHub, click the drop-down next to your profile photo at the top right, and select **Settings > SSH and GPG keys**.
2. Click **New SSH key**.
3. In WSL, enter the following to print the SSH key in your terminal:

    ```
    cat ~/.ssh/id_ed25519.pub
    ```

4. Copy and paste the key from your WSL terminal to the **Key** text box on GitHub and enter a memorable name for the key in the **Title** field. Click **Add SSH key** to save it.

### Fork or clone the Axway-Open-Docs Git repository

You have two options to clone the the [axway-open-docs Git repo](https://github.com/Axway/axway-open-docs) to your local machine:

1. Clone the Axway-Open-Docs repository directly. This requires that you have write permissions on the repository to make any changes.
2. Fork (make a copy) of the Axway-Open-Docs repository in your personal GitHub account and clone the fork. To fork the repository, follow the steps in [Fork a repo](https://help.github.com/en/github/getting-started-with-github/fork-a-repo).

To clone the Axway-Open-Docs repository directly, enter the following commands in WSL:

```
cd ~
git clone git@github.com:Axway/axway-open-docs.git
```

If you have forked the Axway-Open-Docs repository, enter the following commands to clone your _fork_ of the repo instead:

```
cd ~
git clone git@github.com:YOUR-USERNAME/axway-open-docs.git
```

After running these commands, you will have a local copy of the repository in the following location:

```
/home/YOUR-UNIX-USERNAME/axway-open-docs
```

### Install Hugo

You need a recent **extended** version (version 0.53 or later) of Hugo to build and run the site. If you install from the [Hugo releases page](https://github.com/gohugoio/hugo/releases), make sure to get the `extended` Hugo version, which supports SCSS.

Enter the following commands in WSL to download and unpack the Linux 64 bit deb package:

```
wget https://github.com/gohugoio/hugo/releases/download/v0.56.3/hugo_extended_0.56.3_Linux-64bit.deb
sudo dpkg -i hugo_extended_0.56.3_Linux-64bit.deb
```

{{% alert title="Note" %}}
Do not use `sudo apt-get install hugo` to install on Linux, as it does not always get you the `extended` version.
{{% /alert %}}

For full installation instructions for other platforms, see [Install Hugo](https://gohugo.io/getting-started/installing/).

#### Upgrade Hugo

To upgrade to a later version of Hugo, for example v0.66.0, enter the following commands to install the later version over your existing version:

```
wget https://github.com/gohugoio/hugo/releases/download/v0.66.0/hugo_extended_0.66.0_Linux-64bit.deb
sudo dpkg -i hugo_extended_0.66.0_Linux-64bit.deb
```

To verify what version of Hugo you are running, enter:

```
$ which hugo
/usr/local/bin/hugo
$ hugo version
Hugo Static Site Generator v0.66.0-78C3C78F/extended linux/amd64 BuildDate: 2020-03-03T15:28:32Z
```

### Install NodeJS

You need a recent version (10.x or later) of [NodeJS](https://nodejs.org/en/). The `build.sh` script uses NodeJS to install PostCSS, which is required to run the Docsy theme submodule.

Enter the following commands in WSL to install NodeJS version 10.x:

```
curl -sL https://deb.nodesource.com/setup_10.x | sudo -E bash -
sudo apt-get install -y nodejs
```

See [Node.js Binary Distributions](https://github.com/nodesource/distributions/blob/master/README.md) for instructions for installing other versions on Ubuntu.

## Build the site locally

Run the `build.sh` script to build your site locally:

```
cd ~/axway-open-docs/
./build.sh
```

The website is now available locally at `http://localhost:1313/`.

## Make changes locally

You can now add or edit Markdown files in the `content\en\docs\` directory and Hugo will automatically rebuild the site with your changes.

For editing Markdown we recommend using [VSCode](https://code.visualstudio.com/download) with the following extensions:

* [Code Spell Checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker)
* [Markdown Shortcuts](https://marketplace.visualstudio.com/items?itemName=mdickin.markdown-shortcuts)
* [markdownlint](https://marketplace.visualstudio.com/items?itemName=DavidAnson.vscode-markdownlint)
* [Remote Development pack](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.vscode-remote-extensionpack) (work with files on WSL from VSCode on Windows)

When you are ready for your changes to be reviewed:

1. In your Git CLI client, `add`, `commit`, and `push` your files to the remote Git repo.
2. Create a pull request to enable a site maintainer to review the changes you made on your feature branch or fork and _pull_ them into the original Axway repository.

## Protect sensitive information

Install `git-secrets` on your repository to prevent committing secrets and credentials. For more information, see [git-secrets](https://github.com/awslabs/git-secrets).

To install `git-secrets`:

1. Open an Ubuntu WSL window, and change the directory to `axway-open-docs`:

    ```
    cd axway-open-docs
    ```

2. Run the script. You will be asked for your Ubuntu password:

    ```
    bash scripts/git_secrets_setup.sh
    ```

    You should see a result similar to:

    ```
    Clone/update the git-secrets
    Install git-secrets
    [sudo] password for amussap:
    Registering git-secrets as a global option
    Install the git hooks to use with git-secrets
    Success!
    ```

### Test git-secrets

To verify that your `git-secrets` installation is working:

1. Create a feature branch:

    ```
    git checkout -b testgitsecrets
    ```

2. Create or change a file, for example, adding an AWS secret or credential to it.
3. Try to commit your change:

    ```
    git add .
    git commit -m "add AWS key to my page"
    ```

    You should see an error similar to:

    ```
    content/en/docs/contribution_guidelines/testgitsecrets.md:5:AWS_AUTH_ACCESSKEY = <Your AWS authorization key>
    [ERROR] Matched one or more prohibited patterns
    Possible mitigations:
    - Mark false positives as allowed using: git config --add secrets.allowed ...
    - Mark false positives as allowed by adding regular expressions to .gitallowed at repository's root directory
    - List your configured patterns: git config --get-all secrets.patterns
    - List your configured allowed patterns: git config --get-all secrets.allowed
    - List your configured allowed patterns in .gitallowed at repository's root directory
    - Use --no-verify if this is a one-time false positive
    ```

## Tips for configuring Ubuntu WSL

If you are used to working on Windows, Ubuntu WSL can be hard to get used to at first. Follow these tips to make working in Ubuntu easier.

### Work with Windows files from Ubuntu

In Ubuntu WSL your Windows file system (your `c:` drive) is available under the location `/mnt/c`, so for example to access your `Documents` folder on Windows you have to `cd` to `/mnt/c/Users/WINDOWS_USERNAME/Documents/` on WSL.

To make it easier to access Windows files from Ubuntu, you can set up symlinks as follows:

1. Open an Ubuntu WSL window. By default it opens in your Ubuntu home directory (`/home/USERNAME` or the shortcut `~`).
2. Create a symlink to your Windows `Documents` directory:

    ```
    ln -s /mnt/c/Users/WINDOWS_USERNAME/Documents ~/docs
    ```

    This creates a symbolic link to `/mnt/c/Users/WINDOWS_USERNAME/Documents` from `~/docs`. The command does not print any output.

3. After the symlink is created, you can change to your Windows `Documents` directory using the `docs` alias.

    From your home directory in Ubuntu, enter:

    ```
    cd docs
    ```

    Or from any other directory, enter:

    ```
    cd ~/docs
    ```

4. Repeat step 2 to create additional symlinks to the Windows directories that you use most often.

### Configure the Ubuntu prompt

1. Download the file [`git-prompt.sh`](https://github.com/git/git/blob/master/contrib/completion/git-prompt.sh) and save it to your `Documents` directory on Windows. To download the file, right-click the **Raw** button at the top of the file and select **Save link as...**, and then open the file to check that it contains only the raw text and not HTML.
2. Open an Ubuntu WSL window.
3. Copy the `git-prompt.sh` file to the home directory in your Ubuntu file system and rename it as `.git-prompt.sh`:

    ```
    cd ~
    cp /mnt/c/Users/WINDOWS_USERNAME/Documents/git-prompt.sh .git-prompt.sh
    ```

4. Launch Visual Studio Code from Ubuntu:

    ```
    code .
    ```

5. Open the file `.bashrc` in VSCode. This file already exists in your Ubuntu home directory and is run each time you open an Ubuntu window to initialize your shell environment.
6. Paste the following lines at the end of the file:

    ```
    if [ -f ~/.git-prompt.sh ]; then
        source ~/.git-prompt.sh
        export GIT_PS1_SHOWDIRTYSTATE=1
        export PS1='\u@\h \[\033[38;5;11m\]\w\[\033[38;5;14m\]$(__git_ps1 " (%s)")\[\033[00m\]$ '
    fi
    ```

7. Close the current Ubuntu WSL window and open a new one. This forces Ubuntu to load the changes in `.bashrc`.

After completing these steps, the command prompt in Ubuntu shows useful information such as the current Git branch, the status of the working directory, and so on.

## Learn more

* [Hugo documentation](https://gohugo.io/documentation/)
* [Docsy theme documentation](https://www.docsy.dev/docs/)
* [Maintain and customize this site](/docs/contribution_guidelines/maintain_customize/)
