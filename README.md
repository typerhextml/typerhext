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

### Escaping

You can escape some characters with the backslash (`\`).

You are able to escape the following characters:

- new lines, this will just make the compiler ignore there is a new line and just continues to write to the current one.
- backslashes (`\`) as they are used for escaping itself.
