<p align="center">
    <a href="https://typerhext.com/"><img src="./logo.svg" align="center"></a>
    <h1 align="center">THML</h1>
    <p align="center">The TyperHext Markup Language</p>
</p>

<br>
<br>
<br>

## About

TyperHext is a markup language designed to be as powerful as HTML and as simple as Markdown.

**Note:** This is still in development and not ready to use yet, but it will be soon!

## Basic syntax

### Text

You just can simply type any text you want anywhere you want, the HyperText compiler will automatically add paragraphs everytime an empty line is detected. You have to [escape](#escaping) some characters when using plain text.

### Headings

In TyperHext, you can choose from two types of headings: the normal ones and the auto-paragraph headings. Auto-paragraph headings will first create a new paragraph and place themselves in it while normal headings just create a normal heading.

#### Normal headings

| HTML Heading type | TyperHext prefix |
|:---:|:---:|
| P > H1 | `!> ` |
| P > H2 | `!-> ` |
| P > H3 | `!--> ` |
| P > H4 | `!---> ` |
| P > H5 | `!----> ` |
| P > H6 | `!-----> ` |

#### Auto-paragraph headings

> [!WARNING]\
> This type of heading can currently not be converted to HTML because headings are not allowed in paragraphs. See this [StackOverflow answer](https://stackoverflow.com/a/38892009) for more info.
> It's therefore currently not recommended to use them.

| HTML Heading type | TyperHext prefix |
|:---:|:---:|
| H1 | `!- ` |
| H2 | `!-- ` |
| H3 | `!--- ` |
| H4 | `!---- ` |
| H5 | `!----- ` |
| H6 | `!------ ` |

### New lines

If you want to use line breaks in paragraphs, you have to put a full stop (`.`) between the new lines. You even can use multiple of them!

```thml
This is a
.
multiline paragraph.
```

will result in

```html
This is a multiline<br>paragraph.
```

### Bold text

You can use two asterisks (`**`) to make text **bold**. You can use this in Markdown too, but the `__` bold formatting method is not supported in THML.

```thml
This text is **bold**.
```

### Italic text

You can use two underscores (`__`) to make text _italic_. Notice that you cannot use one undescore as in Markdown.

```thml
This text is __italic__.
```

### Special characters

THML is supporting special characters like the rocket emoji (:rocket:), you just have to type in the name of the character and put colons (`:`) before and behind it.

- **[Here is a table containig all special characters with names](./docs/specialcharslist.md)**

Also, you can directly put the Unicode id in the hexadecimal format between the two colons and normal brackets:

```thml
This is the rocket emoji\: :(1f680):
```

### Escaping

You can escape some characters with the backslash (`\`).

You are able to escape the following characters:

- new lines, this will just make the compiler ignore there is a new line and just continues to write to the current one.
- backslashes (`\`) as they are used for escaping itself.
- full stops (`.`) as they are used for new lines [under some conditions](#full-stop-escaping).

#### Full stop escaping

You have to escape full stops if you are using them without other characters in a line.

**Escape required:**
```thml
If you forget to escape the full stop in the next line, it will be converted to a line break.
.
```

**Escape not needed:**
```thml
.thml is a common file ending for TyperHext files
```
or
```thml
TyperHext is cool.
```
