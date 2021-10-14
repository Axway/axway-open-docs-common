---
title: "Maintain and customize Axway-Open-Docs website"
linkTitle: "Maintain and customize"
weight: 5
date: 2019-07-11
description: >
  Understand how to maintain and customize the Axway-Open-Docs website.
---

{{% alert title="Note" %}}
This topic is for documentation site maintainers only!
{{% /alert %}}

If you are a maintainer of this documentation site, this topic includes all the information you need to maintain and customize the site.

## Before you start

* Complete the steps in [Set up and work locally](/docs/contribution_guidelines/setup_work_locally/)

## Overview of tools

This documentation site uses the following tools:

* GitHub - All source files are stored in a Github repo.
* Hugo - The documentation site is built using the Hugo static site generator.
* Docsy - The documentation site uses the Docsy documentation theme from Google.
* Netlify - The site is deployed on Netlify. Deployments are triggered by pushes to GitHub.
* Netlify CMS - Provides a WYSIWYG view of documentation pages.

## Overview of config files

This following configuration files can be found in the site root:

* `config.toml` - Hugo and Docsy theme configuration
* `netlify.toml` - Netlify deployment configuration
* `static/admin/config.js` - Netlify CMS configuration

## Update the Docsy theme

This site uses the [Docsy theme](https://www.docsy.dev/) for Hugo documentation sites. To avail of new features added to the Docsy theme, you must update the theme submodule in the Axway-Open-Docs Git project.

The Docsy theme is installed in this site's Git repo as a Git submodule. To update the theme with the latest commits from the [Docsy GitHub repo](https://github.com/google/docsy):

1. In Git CLI, navigate to the root of the local repo and checkout **master**. For example:

    ```
    cd axway-open-docs
    git checkout master
    ```

2. To update the submodule, run:

    ```
    git submodule update --remote
    ```

3. Add and then commit the change:

    ```
    git add .
    git commit -m "Updating Docsy theme submodule"
    ```

4. Push the commit to your project repo. For example:

    ```
    git push
    ```

5. Tell all project maintainers to run:

    ```
    git checkout master
    git pull
    git submodule update --recursive
    ```

It is not necessary to update the Netlify configuration file with the Docsy version as Git itself keeps track of the submodule version in the Git repository, and Netlify always checks out the latest commit to the Git repository to build and deploy the site.

## Update Hugo version for building on Netlify

This site uses the [Hugo static site generator](https://gohugo.io/) to generate a HTML website from Markdown source. To avail of new features added to Hugo, you must update the Hugo version that is used to build the site on Netlify.

To use a later version of Hugo to build the site on Netlify, change the `HUGO_VERSION` environment variable in the `netlify.toml` configuration file:

```
[build.environment]
HUGO_VERSION = "0.66.0"
```

To ensure that changes you make in your local environment will also work when deployed on Netlify, you must upgrade your local installation of Hugo to the same version as Netlify uses. For details, see [Upgrade Hugo](/docs/contribution_guidelines/setup_work_locally/#upgrade-hugo).

## Create content with the Docsy theme

To learn more about how the content of a Docsy themed website is structured, and how to add different types of content (including documentation pages, blog posts, landing pages, community pages, and even static content), see [Docsy - Adding Content](https://www.docsy.dev/docs/adding-content/content/).

For more information on how the navigation and search work, see [Docsy - Navigation and Search](https://www.docsy.dev/docs/adding-content/navigation/).

## Customize the Docsy theme

This section explains how to customize various elements of the Docsy theme.

### Change colors and fonts

To change the theme colors and fonts, modify the file `assets/scss/_variables_project.scss` as detailed in [Docsy - Look and Feel](https://www.docsy.dev/docs/adding-content/lookandfeel/).

### Change the logo, background image, and favicon

To change the logo, add a logo file as `assets/icons/logo.svg`. This overrides the theme logo.

To change the background image on the home page (`content/en/_index.html`) add an image containing `background` in the file name to the `content/en/` folder, for example, `content\en\featured-background.jpg`.

To change the favicon, add a new favicon in the `static/favicons` directory.

For more details, see [Docsy - Logos and Images](https://www.docsy.dev/docs/adding-content/iconsimages/).

### Change icons

To change a specific Font Awesome icon, such as those used on the [Community](/community/) page, locate an alternative icon on <https://fontawesome.com/> and replace the icon class in the code. The exact steps differ depending on whether the icon is being used in a content page, a shortcode, a partial layout, and so on.

### Add code to head and body end of pages

To add code to the `head` and end of the `body` sections of each page (for example if using Algolia DocSearch or Hotjar), create the files `layouts/partials/hooks/head-end.html` and `layouts/partials/hooks/body-end.html` and add the code in those files. For details, see [Docsy - Add code to head or before body end](https://www.docsy.dev/docs/adding-content/lookandfeel/#add-code-to-head-or-before-body-end).

### Remove the About section

To remove the About section in the main navigation, delete the folder `content\en\about` and set the following parameter in `config.toml`:

```
footer_about_disable = true
```

### Add or change buttons on right navigation

The right nav for each page or post shows **Edit this page** and other buttons.

To change the text of a button:

1. Create an override file `i18n/en.toml`
2. Copy the field to override from `themes/docsy/i18n/en.toml` and edit the string value. For example, to change the Edit button from **Edit this page** to **Improve this page**:

```
[post_edit_this]
other = "Improve this page"
```

To create a new button in the right nav:

1. Create a new partial layout `layouts/partials/page-meta-links.html`
2. Copy the content from `themes/docsy/layouts/partials/page-meta-links.html`
3. Customize the code to implement a new button
4. Add the button text string to `i18n/en.toml`

### Add Analytics and user feedback tracking

For information on enabling Google Analytics tracking and the user feedback widget, see [Docsy - Analytics and User Feedback](https://www.docsy.dev/docs/adding-content/feedback/).

## Add new documentation to Netlify CMS

Whenever you add a new folder of content under `content/en/docs/`, you must define it as a new folder collection in the Netlify CMS configuration to allow contributors to edit the content using Netlify CMS.

To add a new folder collection you must create a new entry in the `collections` array in the CMS configuration file `static/admin/config.js`. The easiest way to do this is to copy and paste an existing folder collection and modify the `contentDirectory`, `imageDirectory` and other fields as appropriate, for example:

```
{
  ...docsDefaults('PATH_TO_DOC_CONTENT', 'PATH_TO_DOC_IMAGES'),
  name: 'USE_LAST_PART_OF_PATH',
  label: 'LABEL_USED_FOR_COLLECTION_IN_LEFT_NAV',
  label_singular: 'LABEL_USED_TO_CREATE_NEW_ITEM_IN_COLLECTION',
  description: 'DESCRIPTION_FOR_COLLECTION',
}
```

For example:

```
{
  ...docsDefaults('apim_policydev/apigw_kps', 'APIGatewayKPSUserGuide'),
  name: 'apigw_kps',
  label: 'Configure KPS',
  label_singular: 'page in KPS section',
  description: 'All pages relating to configuring KPS in Policy Studio.',
}
```

For more details on how collections are defined in Netlify CMS, see [Collection types](https://www.netlifycms.org/docs/collection-types) and [Collections reference](https://www.netlifycms.org/docs/configuration-options/#collections) in Netlify CMS documentation.

<!-- Comment variables out as it's not currently used -->
<!--
## Use variables in content

A list of variables can be found in `axway-open-docs/layouts/shortcodes/variables`, stored as HTML files, where the name of the file is the name of the variable. These HTML files just contain the value of the variable.

Variables are called in Markdown documentation files with the following:

`{{</*  variables/variable_name  */>}}`

Where `variable_name` is the name of the HTML file that contains the variable value, without the `.html` extension.

For example:

`"We love {{< variables/company_name >}} Open Docs!"`

would be written in Markdown as:

`"We love {{</* variables/company_name */>}} Open Docs!"`

Where `company_name` is stored in `axway-open-docs/layouts/shortcodes/variables` as a HTML file called `company_name.html` and simply contains `Axway`.

### Create a new variable

Variables are stored in the `axway-open-docs` project as HTML files.

#### Use file explorer

Navigate to `axway-open-docs/layouts/shortcodes/variables` and create a HTML file. Consider the file name carefully since the shortcode name will mirror that of the file but without the `.html` extension. For example, `axway-open-docs/layouts/shortcodes/variables/company_name.html` will be called with `{{</* variables/company_name */>}}` in the markdown file.

Once you've created the file, open it up with your favorite text editor and simply add the value of the variable into it. For example, `axway-open-docs/layouts/shortcodes/variables/company_name.html` simply contains `Axway`.

#### Use shell

You can customize and run the following bash command (using relative paths):

`echo "Variable value here!" > axway-open-docs/layouts/shortcodes/variables/name_of_variable_file.html`

This will create the HTML file inside of the `shortcodes/variables` directory and add whatever value you want to it.
-->
