---
title: Contribution guidelines
linkTitle: Contribution guidelines
no_list: true
weight: 200
description: |
  How to contribute to Axway-Open-Docs
---
This documentation is open source, and we welcome your interest in contributing to improve the quality of our documentation.

## Before you start

Before you can contribute, you must:

* Create a GitHub account.
* Sign the [Axway Contributor License Agreement (CLA)](https://cla.axway.com/) using your GitHub account email. This is required just once and it should only take a few minutes.
* Read this page in its entirety.
* Familiarize yourself with the [Markdown guidelines](/docs/contribution_guidelines/writing_markdown/) and [best practices for developer documentation](/docs/contribution_guidelines/bestpracticedevdoc/).

{{< alert title="Caution" color="warning">}}
All contributions to this project are public, which means that they are accessible to anyone on the Internet. This includes content in pull requests that are not yet merged or published.

As a result, do not contribute any content containing:

* Information not intended for a public audience, such as proprietary or confidential information.
* Descriptions of security issues or vulnerabilities. Please report any security issues to [Axway Support](https://support.axway.com/) and not as a public GitHub issue.
* Sensitive information such as user names, passwords, keys, and so on.
  {{< /alert >}}

## Different ways you can contribute

To suggest a change to the documentation directly, you can use the following contribution flows:

1. Pull request (PR) via GitHub UI (ideal for small or infrequent changes). See [Option 1 - Edit on GitHub](#option-1-edit-on-github).
2. Pull request via Netlify CMS (WYSIWYG option that does not require any knowledge of Markdown or Git). See [Option 2 - Edit on Netlify CMS](#option-2-edit-on-netlify-cms).

For experienced users, we also support pull requests via Git CLI (ideal for bigger changes or regular updates). See [Set up and work locally](/docs/contribution_guidelines/setup_work_locally).

Finally, if you cannot make a direct contribution, but want to report an issue with this documentation, you can do so using GitHub. See [Create an issue on GitHub](#create-an-issue-on-github).

## Option 1 - Edit on GitHub

All the documentation on this website is written in Markdown. The textual content is stored in the `/content/en/docs/` folder, and the images, in the `/static/Images/` folder.

{{< alert title="Note" color="primary" >}}If you have previously contributed to this project, your fork might be out of sync (behind) the `axway-open-docs` repository. It is best practice to [sync or delete an outdated fork](/docs/contribution_guidelines/deleting_a_repository/) before making a new contribution.{{< /alert >}}

To edit an existing page:

1. Click **Edit on GitHub** on the upper right corner of the page.
2. Click **Fork this repository** to create a copy ([fork](https://help.github.com/en/articles/fork-a-repo)) of the `axway-open-docs` repository in your GitHub account. This allows you to propose changes to a repository that you don't have write access to.
3. Make your changes to the page in the GitHub Markdown editor.

   Click the **Preview changes** tab to quickly check the formatting of your changes.

   ![Preview before creating PR](/Images/contributing/netlify_preview_beforecreating_PR.png)

   This preview does not show your changes as they will appear on the live website, and is useful only for quickly checking standard Markdown formatting (lists, numbering, and so on). You must use the Netlify deploy preview after creating a pull request to fully verify your changes.
4. At the bottom of the page, add a meaningful message describing your change and click **Propose file change**.
5. In the Comparing changes page, check that `Axway/axway-open-docs` is shown on the left, and that your fork is shown on the right, and click **Create pull request**. A pull request enables project maintainers to review the changes you made on your fork and *pull* them into the original repository.

   ![Compare changes and create pull request](/Images/contributing/compare_changes_pr.png)
6. Enter a title (and optionally a description) for the pull request, and click **Create pull request** again. Leave **Allow edits from maintainers** selected, to enable reviewers to make editorial updates to your changes if necessary.

   When you submit a pull request, this triggers a CI flow that runs some checks and builds a preview site containing your changes on Netlify. If your changes fail these checks, you will receive an email notification from GitHub. To get details of the failures and how to fix them, see [PR Run failed email notification](#pr-run-failed-email-notification).
7. To preview your changes exactly as they will appear on the live website, click the deploy preview link:

   ![Preview your PR](/Images/contributing/netlify_preview_PR.png)

   This link opens the home page of the website in the same tab. You must navigate to the page you edited. The number in the deploy preview URL corresponds to the number of the GitHub pull request.

## Option 2 - Edit on Netlify CMS

Use the Netlify CMS user interface to easily edit or create pages in a WYSIWYG editor with a real-time preview.

### Edit an existing page

To edit an existing page:

1. Click **Edit on Netlify CMS** on the upper right corner of the page.
2. Sign in to Netlify CMS using your GitHub account.
3. Click **Fork the repo** to fork (create a copy) of the Axway repository in your GitHub account.

   This option is shown only the first time that you make a contribution.
4. Make your changes in the editor and click **Save**. You can quickly check the formatting in the live preview panel, on the right side.

   This preview does not show all your changes exactly as they will appear on the live website, so it is best to use the Netlify deploy preview after sending your changes for review to fully verify your changes.
5. When you are finished making changes, set the status of the page to **In review**.

   ![Set status to Review](/Images/contributing/netlify_setstatustoreview.png)

   This creates a [pull request](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/about-pull-requests) in the background and triggers an email notification to you and to the project maintainers who will review your changes.

   This also triggers a CI flow that runs some checks and builds a preview site containing your changes on Netlify. If your changes fail these checks, you will receive an email notification from GitHub. When using the CMS, you can ignore any failures as the project maintainers will fix them during their review.
6. To preview your changes exactly as they will appear on the live website, reload the page in the browser and click the new link **Check for Preview**. When the preview is ready, this link changes to **View Preview**.

   ![Preview on CMS](/Images/contributing/cms_deploy_preview.png)
7. To ensure that reviewers have all the information they need to review your changes and to help to speed up the reviewing process, go to the GitHub pull request (using the link received in your email) and add a comment explaining what you changed and why.

### Make further edits after sending for review

Use the Netlify CMS **Workflow** view to easily keep track of the pages you have made changes to and the pages you have sent for review.

* The **Drafts** column lists the pages you have changed but not yet sent for review.
* The **In Review** column lists the pages you have sent for review.

![Workflow](/Images/contributing/netlify_workflowButton.png)

To make further changes to a page, for example, if you forgot to add a detail, or if you noticed a typo:

1. Log in to the [Netlify CMS dashboard](https://axway-open-docs.netlify.app/admin) with your GitHub account.
2. If the page was already sent for review, drag it from the **In Review** column to the **Drafts** column. This lets the reviewer know that you are still working on the page.

   If the page is not listed in the **In Review** column, then it has been merged already and you will need to create a new PR to make further changes. See [Edit an existing page](#edit-an-existing-page).
3. To make further changes, click the page in the **Drafts** column to open it.
4. When you are finished making changes, **Save** the page and set its status to **In review**.
5. Refresh the page and click **Check for Preview/View Preview** to see your changes on the preview website.

{{< alert title="Note" color="primary" >}}
If you notice pages in the **Draft** column of the **Workflow** view that you are not currently working on, these are likely to be from previous contributions that have not been merged. For more information, see [Draft pages in Netlify CMS](#draft-pages-in-netlify-cms).
{{< /alert >}}

### Create a new page

To create a new page:

1. Go to [Netlify CMS](https://axway-open-docs.netlify.com/admin/).
2. Using the left navigation menu, find the section where you want to create the new page.
3. Click **New page in... section** to create a new page in this section.

   ![Create a new page](/Images/contributing/netlify_createNewPage.png)
4. Enter a title and summary for the page.
5. Add the content for the page.
6. **Save** the page, and set its status to **In Review**.
7. Refresh the page and click **Check for Preview/View Preview** to see your changes on the preview website.
8. To ensure that reviewers have all the information they need to review your changes and to help to speed up the reviewing process, go to the GitHub pull request (using the link received in your email) and add a comment explaining what you added and why.

## What to expect when you contribute

When you submit a contribution, the appropriate project maintainers are notified and will respond as quickly as possible. They will review your changes and make additional edits if necessary to ensure that the changes adhere to Axway style and standards.

If a reviewer needs further information about your changes, they will add a comment on the GitHub pull request, which you will receive by email, so it is important that you monitor your GitHub email notifications.

When the review is finished, the reviewer will merge the pull request and publish the changes on [Axway-Open-Docs](https://axway-open-docs.netlify.com), and then on the [Axway Documentation portal](https://docs.axway.com).

## Create an issue on GitHub

If you find an issue or problem in the documentation that you don't know how to fix, create an issue in Axway-Open-Docs GitHub project to report it to us.

When creating a documentation issue, provide as much detail as you can. For example:

* Is it missing important information?
* Does it contain errors or inaccuracies?
* Is it unclear or hard to follow?
* Is it missing examples?
* Does it contain a broken link or broken image link?

The more details you provide, the more helpful the issue, and the faster we can prioritize and fix it.

To create a documentation issue:

1. Click **Create documentation issue** on the upper right corner of any page. You are redirected to GitHub and asked to sign in with your GitHub account.
2. Add a title to the issue. The title of the issue is completed by default with the name of the page, but you can edit it to make it more helpful.
3. Provide detailed information about the problem. A template is provided.

When the issue is created, GitHub sends an email notification to you and to the maintainers of the project. You can also find your issue on the Axway-Open-Docs [list of issues](https://github.com/Axway/axway-open-docs/issues).

The maintainers will review the issue. If the problem is straightforward the maintainers will fix it as soon as possible. If the issue needs further investigation or clarification from a subject matter expert, an internal JIRA ticket will be created and added to the product backlog.

It is important that you monitor your GitHub email notifications to keep informed of any updates to your issue.

## Troubleshooting

The following are some common issues you might encounter when contributing.

### PR Run failed email notification

If you receive this email notification after sending a pull request from GitHub or Git CLI, you should try and address any failures yourself. You can see details of the failures on the **Checks** tab of your pull request in GitHub:

![Failed markdown lint checks](/Images/contributing/failed_checks.png)

{{< alert title="Note" color="primary" >}}
If you are using Netlify CMS, you do not need to worry about these failures, and you are not expected to fix them as it usually requires knowledge of Markdown. The project maintainers will fix these errors when reviewing your contribution.
{{< /alert >}}

### Draft pages in Netlify CMS

If you made a contribution using Netlify CMS and it was not merged and published for some reason (for example, if it was a test contribution), the project maintainers will close the underlying pull request. However, the draft version of the page containing your changes will continue to be available in **Drafts** column of the CMS **Workflow** view.

To abandon the changes permanently, click **Delete changes** to delete the draft:

![Delete a draft](/Images/contributing/cms_workflow_draft.png)

To keep the changes, click the page to open it and make further edits. When you are done, **Save** the page and set its status to **In Review**..