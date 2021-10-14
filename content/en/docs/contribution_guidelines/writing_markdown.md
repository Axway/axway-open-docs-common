---
title: "Markdown guidelines for Axway-Open-Docs"
linkTitle: "Markdown guidelines"
weight: 1
date: 2019-07-30
description: >
  Markdown guidelines and Markdown extensions available for Axway-Open-Docs.
---

This docs-as-code implementation uses the [Hugo](https://gohugo.io/) static site generator and the Google [Docsy theme](https://www.docsy.dev/) to build this website from the Markdown content files. Hugo uses [Goldmark](https://github.com/yuin/goldmark/) to parse Markdown, which is [CommonMark compliant](https://gohugo.io/news/0.60.0-relnotes/).

If you are contributing using GitHub or Git CLI, use these guidelines to ensure that your Markdown renders correctly. You do not need to use these guidelines if you are contributing using Netlify CMS.

## Editor recommendations

If you are editing Markdown locally, we recommend using VSCode with the [`markdownlint` extension](https://github.com/DavidAnson/vscode-markdownlint).

The custom configuration for `markdownlint` is contained in the file `.markdownlint.json` at the root of the [Axway-Open-Docs repository](https://github.com/Axway/axway-open-docs). To load this configuration by default, always open the root folder (`axway-open-docs`) in VSCode.

## Tips and tricks

Follow these tips when sending contributions using Markdown. If there is no explicit rule detailed here, use the recommendations in [Markdown guide - Basic syntax](https://www.markdownguide.org/basic-syntax/).

### Headings

Use hash characters (`#`) for headings. The number of hash characters determines the heading level.

For example:

```md
## This is a H2

This is some text

### This is a H3

This is more text

## This is another H2

This is more text
```

Best practices:

* Do not use H1 headings (`##`) in your Markdown, as the title of the page becomes the H1.
* Do not skip heading levels, that is, do not follow a H2 with a H4.
* Do not use bold or other formatting for headings.

### Emphasis

Surround a word with single underscores (`_`) to apply _italics_ for emphasis.

Surround a word with double asterisks (`**`) to apply **bold** for emphasis.

Best practices:

* Do not overuse emphasis.
* In general, use bold only for UI buttons and fields.
* Use italics only when introducing a new term or to draw extra attention to a word or phrase.

### Blockquotes

Although Markdown supports blockquotes, we generally don't use blockquotes in technical documentation.

### Lists

To create a numbered list add list items with numbers followed by periods. The numbers must be in numerical order.

To create a bulleted list add list items with asterisks (`*`).

To create a nested list, indent the list items by 4 spaces.

#### Definition lists

Use definition lists only for listing terms and associated definitions, such as in a glossary of terms. Do not use definition lists for UI fields and descriptions.

### Inline code

Use single backticks (`` ` ``) to apply code or monospace formatting to a word or phrase within a sentence (inline code). For example, this `command` is inline.

{{% alert title="Caution" color="warning" %}}
The Zoomin plugin used when publishing docs to production <https://docs.axway.com> is very sensitive to `<`, `>`, and `\` characters. Ensure that these characters are always enclosed in backticks to have them processed as code instead of as HTML tags.
{{% /alert %}}

### Code blocks

Use three or more backticks (`` ` ``) to open and close a code sample block.

Specify a programming language after the first set of backticks to apply syntax highlighting. See the supported languages in [List of Chroma Highlighting Languages](https://gohugo.io/content-management/syntax-highlighting/#highlighting-in-code-fences).

Here's an example of a code sample with `java` syntax highlighting:

```md
    ```java
    public class MyClass {
        public static void main(String[] args) {
            System.out.println("Hello World");
        }
    }
    ```
```

This renders as:

```java
public class MyClass {
    public static void main(String[] args) {
        System.out.println("Hello World");
    }
}
```

Best practices:

* Do use code block styling for single and multiple-line code blocks.
* Do not use inline code styling for single line code blocks.

{{% alert title="Note" color="primary" %}}
Do not use indentation to create code blocks. Markdown syntax allows you to create code blocks by indenting all lines in the code block by four spaces or one tab, however using indentation rather than backticks can cause issues with nesting code blocks inside lists, and with publishing on production.
{{% /alert %}}

### Links

To create a link, enclose the link text in square brackets and follow it with the URL in parentheses.

For example, `[contribution guidelines](/docs/contribution_guidelines/)` is rendered as [contribution guidelines](/docs/contribution_guidelines/).

Use relative paths for all internal links.

### Images

To add an image, use an exclamation mark (`!`), followed by alt text in square brackets, and the path to the image in parentheses, for example `![Image alt text](/Images/MyFolder/MyImage.png)`.

Add new images to the `static/Images` folder in the project, but note that the path to these images in the rendered site is just `Images`. For example, to add an image stored in `static/Images/MyImage.png` the correct image reference is `![My image alt text](/Images/MyImage.png)` and not `![My image alt text](/static/Images/MyImage.png)`

### HTML

We do not allow any HTML tags within Markdown contributions, as HTML tags can be used in security attacks.

### Tables

Markdown has limited support for tables. We support only pipe tables as described in [Tables](https://www.markdownguide.org/extended-syntax/#tables).

Table cells cannot contain multiple paragraphs, or code blocks, or lists. If you require a more complex table, consider using lists or alternative formatting instead.

If you have a simple table from another source (for example, Microsoft Excel) that you want to use in Markdown format, we recommend the [Markdown Tables Generator](https://www.tablesgenerator.com/markdown_tables).

## Markdown extensions

Hugo and Docsy provide some useful extensions to standard Markdown that you can use to simplify editing and formatting.

### Notes or alerts

Use an _alert shortcode_ to draw the reader's attention to something. For example:

For example:

```go-html-template
{{%/* alert title="Note" */%}}
This is a note.
{{%/* /alert */%}}

```

This renders to:

{{% alert title="Note" %}}
This is a note.
{{% /alert %}}

See [Docsy alert shortcode](https://www.docsy.dev/docs/adding-content/shortcodes/#alert) for more details.

Best practices:

* Do not use any other styling to highlight information, such as bold, bullet lists, and so on. To draw attention to something, always use an alert.

### YouTube video links

To display a YouTube video preview on a page, use the following _Hugo shortcode_. You only need to specify the ID of the video.

For example:

```go-html-template
{{</* youtube Dq7GwLvRhLg */>}}
```

This renders to:

{{< youtube Dq7GwLvRhLg >}}

See [Hugo YouTube shortcode](https://gohugo.io/content-management/shortcodes/#youtube) for more details.

## Learn more

* [The Markdown Guide](https://www.markdownguide.org/)
