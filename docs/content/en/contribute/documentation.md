---
title: Documentation
description: Help us to improve the documentation by identifying issues and suggesting changes.
categories: [contribute]
keywords: [documentation]
menu:
  docs:
    parent: contribute
    weight: 30
weight: 30
toc: true
aliases: [/contribute/docs/]
---

## Introduction

We welcome corrections and improvements to the documentation. Please note that the documentation resides in its own repository, separate from the project repository.

For corrections and improvements to the current documentation, please submit issues and pull requests to the [documentation repository].

For documentation related to a new feature, please include the documentation changes when you submit a pull request to the [project repository].

## Guidelines

### Style

Please adhere to Google's [developer documentation style guide].

[developer documentation style guide]: https://developers.google.com/style

### Markdown

Please follow these guidelines:

- Use [ATX] headings, not [setext] headings, levels 2 through 4
- Use [fenced code blocks], not [indented code blocks]
- Use hyphens, not asterisks, with unordered [list items]
- Use the [note shortcode] instead of blockquotes or bold text
- Do not mix [raw HTML] within Markdown
- Do not use bold text instead of a heading or description term (`dt`)
- Remove consecutive blank lines (maximum of two)
- Remove trailing spaces

### Glossary

Glossary terms are maintained on individual pages. While not directly accessible to site visitors, these pages act as a central repository for term definitions.

Definitions must be presented in complete sentences, with the first sentence always introducing the term being defined. To enhance readability and consistency, the first occurrence of the term and any other referenced glossary terms should be italicized.

To link to a term definition on the glossary page, use this custom link syntax:

```text
[term](g)
```

Lookups are case-insensitive, ignore formatting, and support both singular and plural forms. For example, all of these variations will link to the same glossary term:

```text
[global resource](g)
[Global Resource](g)
[Global Resources](g)
[`Global Resources`](g)
```

To insert a term definition, use the [`glossary-term`] shortcode:

```text
{{%/* glossary-term "global resource" */%}}
```

### Terminology

Please link to the glossary (see above) when necessary, and use the terms consistently throughout the documentation. Of special note:

- The term "front matter" is two words unless you are referring to the configuration key
- The term "home page" is two words
- The term "website" is one word
- The term "standalone" is one word, not hyphenated
- Use the word "map" instead of "dictionary"
- Use the word "flag" instead of "option" when referring to a command line flag
- Use "client side" as a noun, and "client-side" as an adjective
- Capitalize the word "Markdown"
- Hyphenate the term "open-source" when used an adjective.

### Page titles and headings

Please follow these guidelines for page titles and headings:

- Use sentence-style capitalization
- Avoid formatted strings in headings and page titles
- Shorter is better

### Use active voice with present tense

In software documentation, passive voice is unavoidable in some cases. Please use active voice when possible.

No → With Hugo you can build a static site.\
Yes → Build a static site with Hugo.

No → This will cause Hugo to generate HTML files in the `public` directory.\
Yes → Hugo generates HTML files in the `public` directory.

### Use second person instead of third person

No → Users should exercise caution when deleting files.\
Better → You must be cautious when deleting files.\
Best → Be cautious when deleting files.

### Avoid adverbs when possible

No → Hugo is extremely fast.\
Yes → Hugo is fast.

{{% note %}}
"It's an adverb, Sam. It's a lazy tool of a weak mind." (Outbreak, 1995).
{{% /note %}}

### Level 6 headings

Level 6 headings are styled as `dt` elements. This was implemented to support a [glossary] with linkable terms.

### Function and method descriptions

When adding a page to the [functions] or [methods] section, begin the description with the word "Returns". With functions and methods that return a boolean value, begin the description with the phrase "Reports whether".

For example:

- `Returns the URL aliases as defined in front matter.`
- `Reports whether the given page is in the given section.`

[functions]: /functions
[methods]: /methods

### Directory names, file names, and file paths

Enclose directory names, file names, and file paths within backticks, with the following exceptions:

- Page titles
- Section headings (h1-h6)
- Definition list terms
- The description field in front matter

### Miscellaneous

Other guidelines to consider:

- Do not place list items directly under a heading; include an introductory sentence or phrase before the list.
- Avoid use of **bold** text. Use the [note shortcode] to draw attention to important content.
- Do not place description terms (`dt`) within backticks unless required for syntactic clarity.
- Do not use Hugo's `ref` or `relref` shortcodes. We use a link render hook to resolve and validate link destinations, including fragments.
- Shorter is better. If there is more than one way to do something, describe the current best practice. For example, avoid phrases such as "you can also do..." and "in older versions you had to..."
- When including code samples, use short snippets that demonstrate the concept.
- The Hugo user community is global; use  [basic english](https://simple.wikipedia.org/wiki/Basic_English) when possible.

## Code examples

Indent code by two spaces. With examples of template code, include a space after opening action delimiters, and include a space before closing action delimiters.

### Fenced code blocks

Always include the language code when using a fenced code block:

````text
```go-html-template
{{ if eq $foo "bar" }}
  {{ print "foo is bar" }}
{{ end }}
```
````

```go-html-template
{{ if eq $foo "bar" }}
  {{ print "foo is bar" }}
{{ end }}
```

### Shortcode calls

Use this syntax to include shortcodes calls within your code examples:

```text
{{</*/* foo */*/>}}
{{%/*/* foo */*/%}}
```

```text
{{</* foo */>}}
{{%/* foo */%}}
```

### Site configuration

Use the [code-toggle shortcode] to include site configuration examples:

```text
{{</* code-toggle file=hugo */>}}
baseURL = 'https://example.org/'
languageCode = 'en-US'
title = 'My Site'
{{</* /code-toggle */>}}
```

{{< code-toggle file=hugo >}}
baseURL = 'https://example.org/'
languageCode = 'en-US'
title = 'My Site'
{{< /code-toggle >}}

### Front matter

Use the [code-toggle shortcode] to include front matter examples:

```text
{{</* code-toggle file=content/posts/my-first-post.md fm=true */>}}
title = 'My first post'
date = 2023-11-09T12:56:07-08:00
draft = false
{{</* /code-toggle */>}}
```

{{< code-toggle file=content/posts/my-first-post.md fm=true >}}
title = 'My first post'
date = 2023-11-09T12:56:07-08:00
draft = false
{{< /code-toggle >}}

### Other code examples

Use the [code shortcode] for other code examples that require a file name:

```text
{{</* code file=layouts/_default/single.html */>}}
{{ range .Site.RegularPages }}
  <h2><a href="{{ .RelPermalink }}">{{ .LinkTitle }}</a></h2>
{{ end }}
{{</* /code */>}}
```

{{< code file=layouts/_default/single.html >}}
{{ range .Site.RegularPages }}
  <h2><a href="{{ .RelPermalink }}">{{ .LinkTitle }}</a></h2>
{{ end }}
{{< /code >}}

## Shortcodes

These shortcodes are commonly used throughout the documentation. Other shortcodes are available for specialized use.

### code

Use the `code` shortcode for other code examples that require a file name. See the [code examples] above. This shortcode takes these arguments:

copy
: (`bool`) Whether to display a copy-to-clipboard button. Default is `false`.

file
: (`string`) The file name to display.

lang
: (`string`) The code language. If you do not provide a `lang` argument, the code language is determined by the file extension. If the file extension is `html`, sets the code language to `go-html-template`. Default is `text`.

```text
{{</* code file=content/something/foo.md lang=text copy=true */>}}
Some code here
{{</* /code */>}}
```

{{< code file=content/something/foo.md lang=text copy=true >}}
Some code here
{{< /code >}}

### code-toggle

Use the `code-toggle` shortcode to display examples of site configuration, front matter, or data files. See the [code examples] above. This shortcode takes these arguments:

config
: (`string`) The section of `site.Data.docs.config` to render.

copy
: (`bool`) Whether to display a copy-to-clipboard button. Default is `false`.

file
: (`string`) The file name to display. Omit the file extension for site configuration examples. Default is `hugo`

fm
: (`bool`) Whether the example is front matter. Default is `false`.

skipHeader
: (`bool`) Whether to omit top level key(s) when rendering a section of `site.Data.docs.config`.

```text
{{</* code-toggle */>}}
title: Example
draft: false
{{</* /code-toggle */>}}
```

{{< code-toggle >}}
title: Example
draft: false
{{< /code-toggle >}}

### deprecated-in

Use the `deprecated-in` shortcode to indicate that a feature is deprecated:

```text
{{%/* deprecated-in 0.127.0 */%}}
Use [`hugo.IsServer`] instead.

[`hugo.IsServer`]: /functions/hugo/isserver/
{{%/* /deprecated-in */%}}
```

{{% deprecated-in 0.127.0 %}}
Use [`hugo.IsServer`] instead.

[`hugo.IsServer`]: /functions/hugo/isserver/
{{% /deprecated-in %}}

### eturl

Use the embedded template URL (`eturl`) shortcode to insert an absolute URL to the source code for an embedded template. The shortcode takes a single argument, the base file name of the template (omit the file extension).

```text
This is a link to the [embedded alias template].

[embedded alias template]: {{%/* eturl alias */%}}
```

This is a link to the [embedded alias template].

[embedded alias template]: {{% eturl alias %}}

### glossary-term

Use the `glossary-term` shortcode to insert the definition of the given glossary term.

```text
{{%/* glossary-term scalar */%}}
```

{{% glossary-term scalar %}}

### include

Use the `include` shortcode to include content from another page.

```text
{{%/* include "functions/_common/glob-patterns" */%}}
```

### new-in

Use the `new-in` shortcode to indicate a new feature:

```text
{{</* new-in 0.127.0 */>}}
```

{{< new-in 0.127.0 />}}

### note

Use the `note` shortcode with `{{%/* */%}}` delimiters to call attention to important content:

```text
{{%/* note */%}}
Use the [`math.Mod`] function to control...

[`math.Mod`]: /functions/math/mod/
{{%/* /note */%}}
```

{{% note %}}
Use the [`math.Mod`] function to control...

[`math.Mod`]: /functions/math/mod/
{{% /note %}}

## New features

Use the "new-in" shortcode to indicate a new feature:

{{< code file=content/something/foo.md lang=text >}}
{{</* new-in 0.120.0 */>}}
{{< /code >}}

The "new in" label will be hidden if the specified version is older than a predefined threshold, based on differences in major and minor versions. See&nbsp;[details](https://github.com/gohugoio/hugoDocs/blob/master/_vendor/github.com/gohugoio/gohugoioTheme/layouts/shortcodes/new-in.html).

## Deprecated features

Use the "deprecated-in" shortcode to indicate that a feature is deprecated:

{{< code file=content/something/foo.md >}}
{{%/* deprecated-in 0.120.0 */%}}
Use [`hugo.IsServer`] instead.

[`hugo.IsServer`]: /functions/hugo/isserver/
{{%/* /deprecated-in */%}}
{{< /code >}}

When deprecating a function or method, add something like this to front matter:

{{< code-toggle file=content/something/foo.md fm=true >}}
expiryDate: 2024-10-30 # deprecated 2022-10-30 in v0.123.0
{{< /code-toggle >}}

Set the `expiryDate` to two years from the date of deprecation, and add a brief front matter comment to explain the setting.

## GitHub workflow

{{% note %}}
This section assumes that you have a working knowledge of Git and GitHub, and are comfortable working on the command line.
{{% /note %}}

Use this workflow to create and submit pull requests.

Step 1
: Fork the [documentation repository].

Step 2
: Clone your fork.

Step 3
: Create a new branch with a descriptive name that includes the corresponding issue number, if any:

```sh
git checkout -b restructure-foo-page-99999
```

Step 4
: Make changes.

Step 5
: Build the site locally to preview your changes.

Step 6
: Commit your changes with a descriptive commit message:

- Provide a summary on the first line, typically 50 characters or less, followed by a blank line.
- Optionally, provide a detailed description where each line is 80 characters or less, followed by a blank line.
- Optionally, add one or more "Fixes" or "Closes" keywords, each on its own line, referencing the [issues] addressed by this change.

For example:

```sh
git commit -m "Restructure the taxonomy page

This restructures the taxonomy page by splitting topics into logical
sections, each with one or more examples.

Fixes #9999
Closes #9998"
```

Step 7
: Push the new branch to your fork of the documentation repository.

Step 8
: Visit the [documentation repository] and create a pull request (PR).

Step 9
: A project maintainer will review your PR and may request changes. You may delete your branch after the maintainer merges your PR.

[ATX]: https://spec.commonmark.org/0.30/#atx-headings
[Microsoft Writing Style Guide]: https://learn.microsoft.com/en-us/style-guide/welcome/
[`glossary-term`]: #glossary-term
[basic english]: https://simple.wikipedia.org/wiki/Basic_English
[code examples]: #code-examples
[code shortcode]: #code
[code-toggle shortcode]: #code-toggle
[documentation repository]: https://github.com/gohugoio/hugoDocs/
[fenced code blocks]: https://spec.commonmark.org/0.30/#fenced-code-blocks
[glossary]: /quick-reference/glossary/
[indented code blocks]: https://spec.commonmark.org/0.30/#indented-code-blocks
[issues]: https://github.com/gohugoio/hugoDocs/issues
[list items]: https://spec.commonmark.org/0.30/#list-items
[note shortcode]: #note
[project repository]: https://github.com/gohugoio/hugo
[raw HTML]: https://spec.commonmark.org/0.30/#raw-html
[setext]: https://spec.commonmark.org/0.30/#setext-heading
