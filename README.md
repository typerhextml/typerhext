<p align="center">
    <a href="https://typerhext.com/"><img src="https://raw.githubusercontent.com/typerhextml/logos/main/svg/logo.svg" alt="TyperHext" align="center"></a>
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

These headers will only work when the line they're in is empty.

**Note:** It's recommended to use the H1-Headings only once in a document, just like in HTML. For bigger text, you should use styling.

| HTML syntax | TyperHext syntax |
|:---:|:---:|
| `<h1>Heading 1</h1>` | `=== Heading 1 ===` |
| `<h2>Heading 2</h2>` | `== Heading 2 ==` |
| `<h3>Heading 3</h3>` | `= Heading 3 =` |
| `<h4>Heading 4</h4>` | `--- Heading 4 ---` |
| `<h5>Heading 5</h5>` | `-- Heading 5 --` |
| `<h6>Heading 6</h6>` | `- Heading 6 -` |

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

Both notations are case-insensitive.

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

### Tagging

You are able to tag blocks in THML with a CSS-like selector syntax using sqare brackets. This syntax is really useful combined with [styling](#styling).

>[!TIP]
>Tag blocks use `span` on the text level and `div` on the block level if not specified.
>
>If you want to enforce a `div` block, type `[- #my-id]`.
>
>If you want to enforce a `span` block, type `[~ #my-id]`.

| HTML | TyperHext | CSS |
|:---:|:---:|:---:|
| `id="my-id"` | `#my-id` | `#my-id` |
| `class="my-class"` | `.my-class` | `.my-class` |
| `class="my-class1 my-class2"` | `.my-class1.my-class2` | `.my-class1.my-class2` |
| `my-tag="yes"` | `my-tag: yes` | `[my-tag="yes"]` |
| `my-tag` | `my-tag` | `[my-tag]` |

```thml
[#my-id]This block has the ID <my-id>.

[.my-class]This part of the block has the class <my-class>.[/] And this part doesn't.

[.my-class2 /]This block has the class <my-id2>.

And this one too![/]

[div]This is not a div! It will get the tag <div>.

[#my-id2.my-class3.my-class4; aria-label: My custom label!; custom-attr: mytext]This has lots of tags applied.

[/]Error: nothing to close.
```

### Hyperlinks

You can add hyperlinks to blocks. The TyperHext compiler decides how it will compile the code into HTML like that:

>[!NOTE]
>Tag blocks work the same way.

**Example 1:**

```thml
Link []in[/]@https://typerhext.com/@ text
```

will compile to

```html
<p>
    Link <a href="https://typerhext.com/">in</a> text
</p>
```

**Example 2:**

```thml
Link [#mylink]in[/]@https://typerhext.com/@ text with tags
```

will compile to

```html
<p>
    Link <a href="https://typerhext.com/" id="mylink">in</a> text
</p>
```

**Example 3:**

```thml
[]@https://typerhext.com/@Link as block
```

will compile to

```html
<a href="https://typerhext.com/">
    <p>
        Link as block
    </p>
</a>
```

**Example 4:**

```thml
[ /]@https://typerhext.com/@Link over

multiple blocks[/]
```

will compile to

```html
<a href="https://typerhext.com/">
    <p>
        Link over
    </p>
    <p>
        multiple blocks
    </p>
</a>
```

### Styling

THML supports CSS, SCSS and SASS styling. To open a style block, start with `%<styling language>` and end it with a single `%`.

**Example:**
```thml
%scss
    .important {
        color: red;
        font-weight: 700;
    }
%

[.important]Important:[/] TyperHext supports styling.
```
