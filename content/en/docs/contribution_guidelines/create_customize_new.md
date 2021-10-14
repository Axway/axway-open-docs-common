---
title: "Create and customize a new documentation project"
linkTitle: "Create and customize a new project"
draft: true
weight: 6
date: 2020-03-24
description: >
  Understand how to create and customize your own documentation project.
---

This section provides detailed steps for you to create and customize your own documentation project using the same tools as this project. This is intended for use by other teams who want to open source their documentation and enable contributions using GitHub and Netlify CMS.

## Before you start

You must have completed all of the steps in [Set up and work locally](/docs/contribution_guidelines/setup_work_locally/). The following steps assume you have a clone or fork of the Axway-Open-Docs repository available locally.

## Create a new documentation project

This section shows how to create a new project based on the `docsy-example` project that Axway-Open-Docs is based on.

### Fork and rename the `docsy-example` project

1. Go to the [docsy-example project on GitHub](https://github.com/google/docsy-example).
2. Fork the project to your personal GitHub account. Your fork is now available at the URL `https://github.com/USERNAME/docsy-example`.
3. Go to your fork on GitHub and click **Settings**.
4. Enter a new name (for example, `open-docs-MYPROJECT`) in the **Repository name** field and click **Rename**. Your fork is now available at the URL `https://github.com/USERNAME/open-docs-MYPROJECT`.

### Clone your fork

Enter the following commands in Ubuntu WSL to clone your fork:

```
cd ~
git clone --recurse-submodules --depth 1 git@github.com:YOUR-USERNAME/open-docs-MYPROJECT.git
```

{{% alert title="Note" %}}
You must use `--recurse-submodules` or you will not pull down the Docsy theme code you need to generate a working site.
{{% /alert %}}

After running these commands, you will have a local copy of the repository in the following location:

```
/home/YOUR-UNIX-USERNAME/open-docs-MYPROJECT
```

### Build the site locally

Run the `hugo server` command in your site root:

```
cd ~/open-docs-MYPROJECT/
hugo server
```

The website is now available locally at `http://localhost:1313/`.

## Customize the new project

This section shows how to customize the new project with the project-specific settings and with the same look-and-feel and functionality as Axway-Open-Docs.

### Copy and update `config.toml`

The `config.toml` file contains configuration settings for Docsy and Hugo.

To use the custom settings from Axway-Open-Docs, replace the `config.toml` file in your project with the Axway-Open-Docs `config.toml`:

```
cd ~/open-docs-MYPROJECT/
cp ~/axway-open-docs/config.toml .
```

Next, open the `config.toml` file in VSCode and edit the following settings.

`baseURL`
: Set this to `https://axway-open-docs-MYPROJECT.netlify.com/`

`[params]`
: Set the `github_repo` field to the URL of your new GitHub project, for example, `https://github.com/USERNAME/open-docs-MYPROJECT`.

### Copy layout and CSS customizations

Copy the folders `layouts`, `assets`, and `i18n` from Axway-Open-Docs to your project:

```
cd ~/open-docs-MYPROJECT/
cp -r ~/axway-open-docs/layouts/ .
cp -r ~/axway-open-docs/assets/ .
cp -r ~/axway-open-docs/i18n/ .
```

### Copy images and favicon

Copy the home page background image from Axway-Open-Docs to your project, and remove the Docsy background image:

```
cd ~/open-docs-MYPROJECT/content/en/
cp ~/axway-open-docs/content/en/big-idea-background.jpg .
rm featured-background.jpg
```

Copy the favicon from Axway-Open-Docs to your project:

```
cd ~/open-docs-MYPROJECT/
mkdir static
cd static/
mkdir favicons
cd favicons/
cp ~/axway-open-docs/static/favicons/favicon.ico .
```

### Install PostCSS for your new project

Enter the following commands to install PostCSS using `npm`:

```
cd ~/open-docs-MYPROJECT
sudo npm install -D --save autoprefixer
sudo npm install -D --save postcss-cli
```

If these commands report errors first time, trying them again a second time should work for some unknown reason!

### Check how the site looks

At this point, you've customized everything except the content of the site, and it should look a lot like the Axway-Open-Docs now, so run the `hugo server` command in your site root to find out:

```
cd ~/open-docs-MYPROJECT/
hugo server
```

Open `http://localhost:1313/` and you should see something like this:

![Customized Docsy Example Site](/Images/contributing/docsy_example_customized.png)
