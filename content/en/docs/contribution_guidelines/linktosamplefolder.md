---
title: "Draft - Link to Samples folder"
linkTitle: "Draft - Link to Samples folder"
weight: 100
date: 2021-08-18
description: >
  Link to Samples folder - test for Zoomin
---

## Link using absolute path

{{< alert title="Warning" color="warning" >}} That's the way it works today {{< /alert >}}

This is a link using absolute path, which we **don't** want -> Click to download [create_environments.json](https://axway-open-docs.netlify.app/samples/central/create_environments.json).

The code of the link is:

```
[create_environments.json](https://axway-open-docs.netlify.app/samples/central/create_environments.json)
```

## Link using relative path

{{< alert title="Note" color="primary" >}}That's what we want{{< /alert >}}

This is a link using **relative** path, which we want -> Click to download [create_environments.json](/samples/central/create_environments.json).

The code of the link is:

```
[create_environments.json](/samples/central/create_environments.json)
```

This link works on Netlify but not on Zoomin.

## Test - add Samples folder under Images folder

{{< alert title="Note" color="primary" >}} This is a test just to see if it works, but we won't keep this structure. {{< /alert >}}

Click to download [create_environments2.json](/Images/samplestest/central/create_environments2.json).

The code of the link is:

```
[create_environments.json](/images/samplestest/central/create_environments2.json)
```

## Link to an image

![Preview your PR](/Images/contributing/netlify_preview_PR.png)

The code of the link is:

```
![Preview your PR](/Images/contributing/netlify_preview_PR.png)
```

Testing HTML tags.
<br>
Another test: Go to the <a href="http://axway.com/" target="_blank">Axway doc site</a>