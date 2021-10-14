---
title: "Sync or delete an outdated fork before contributing"
linkTitle: "Sync or delete an outdated fork"
weight: 6
date: 2019-10-15
description: >
    To avoid issues when sending a pull request, make sure that your fork is up to date with the upstream repository before contributing to the documentation.
---

The first time you make a contribution to the documentation by way of GitHub or Netlify CMS, this creates a copy (fork) of the [axway-open-docs](https://github.com/Axway/axway-open-docs) repository in your GitHub account.

Since there are other users collaborating with Axway documentation, it is highly likely that your fork will quickly fall behind the upstream repository and you might encounter conflicts the next time you try to send a pull request.

To avoid issues when sending a pull request, you can [delete and recreate](#delete-and-recreate-your-fork) using the GitHub UI, or [synchronize](#sync-your-fork) your fork using Git CLI, before starting a new contribution.

{{< alert title="Note" color="primary">}} You do not need to sync your fork if you are working exclusively from Netlify CMS, as Netlify CMS creates the new branch based on master from the upstream repository.{{< /alert >}}

## Delete and recreate your fork

{{< alert title="Caution" color="warning">}}Do not delete your fork if you have pending PRs that have not yet been merged, as the changes from those PRs will be lost.{{< /alert >}}

To delete and recreate your fork before you make a new contribution:

1. Go to your `axway-open-docs` fork on GitHub, and click **Settings**

    ```
    https://github.com/YOUR-USERNAME/axway-open-docs
    ```

    ![Delete fork Settings](/Images/contributing/deletefork_settings.png)

2. Under Danger Zone, click **Delete this repository**.

    ![Delete fork Danger Zone](/Images/contributing/deletefork_dangerzone.png)

3. Follow the [Edit on GitHub](/docs/contribution_guidelines/#option-1-edit-on-github) procedure to start a new contribution, which creates a new fork based on the latest upstream.

To find out more about how to delete your fork, see [Deleting a repository](https://help.github.com/en/articles/deleting-a-repository).

## Sync your fork

You can sync your fork with the latest changes added to the upstream repository, using Git on the command line. For details, see [Keep your fork synced](https://help.github.com/en/articles/fork-a-repo#keep-your-fork-synced).
