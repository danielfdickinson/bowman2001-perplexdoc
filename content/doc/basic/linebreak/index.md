---
title: Line Break
description: A break inside a paragraph
subtitle: false
date: '2021-03-24T13:17:56+01:00'
weight: 111
authors:
- Georg Makowski
categories:
- Markdown
tags:
- linebreak
- inline
menu:
  doc:
    name: Line Break
    parent: basic
    pre: drag_handle
---

Sometimes we like to begin a new line without starting a whole new text block. Placing such a hard-line break gets complicated when **hard-line wraps** determine the line length inside the Markdown content files.
{.p-first} <!--more-->

## Syntax

There are two ways to place intentional hard-line breaks, which depend on the way we handle hard-line wraps.

CommonMark
: allows **hard wraps** — a.&hairsp;k.&hairsp;a. hard-line breaks — to limit the line length. They are treated just like spaces. Therefore, CommonMark needs a special syntax element for an intentional line break.

GitHub
: instead, treats hard-line breaks simply as such. In this case, we should probably enable **soft wraps** in our editor to limit the line length and avoid horizontal scrolling. (See also: [Writing Markdown][hwl])
{.dl-loose}

### The CommonMark Way

Hugo’s standard configuration is fully CommonMark-compliant, the parameter `hardWraps` is set to `false` by default. There are two ways now, to place an intentional line break:

Two spaces `  `
: before the end of a line.

One backslash `\`
: directly after the text and before the end of the line.
{.dl-loose}

Both options are error-prone. Spaces before the end of the line are usually invisible in text editors and get easily deleted by accident. The backslash is visible, but if there’s only one additional space character between the backslash and the also invisible newline character, the backslash is treated literally. And we get a visible `\` instead of a newline on the page.

### The GitHub Way

To format line breaks like GitHub, we need to set `hardWraps` to `true`, as in the [configuration for this project][hw]. Now, the syntax becomes intuitive:

Hard line breaks
: break lines hard.
{.dl-loose}

If we change the line-breaking from CommonMark’s way to GitHub’s, Hugo still recognizes the CommonMark breaks. We don’t need to replace them. But we need to remove simple breaks because they are now all treated as intentional ones.

### What now?

When you have to strictly adhere to the CommonMark specification the best option from my point of view is still, to forgo hard wraps and use CommonMark breaks. This way is compatible with CommonMark **and** GitHub.

When you are allowed to deviate from CommonMark regarding this one element, I strongly recommend the GitHub way. (See also: [Writing Markdown][hwl])

## Layout

There shouldn’t be any difference in the rendered result. You need to check the file {$content/doc/basic/linebreak/index.md} to see the different syntax options in the Markdown content.

### Line Break {.h-p}
{{% pangram %}}
{{% pangram 2 %}}
{.placeholder data-pagefind-ignore="all"}

### Two spaces {.h-p}
{{% pangram %}}  
{{% pangram 2 %}}
{.placeholder data-pagefind-ignore="all"}

### Backslash {.h-p}
{{% pangram %}}\
{{% pangram 2 %}}
{.placeholder data-pagefind-ignore="all"}

[hw]: /doc/appendix/config/markup#24

[hwl]: /doc/intro/markdown#wrap
