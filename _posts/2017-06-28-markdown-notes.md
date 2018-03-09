---
layout: post
title: Markdown Basics ref notes.
date: 2017-06-28 14:32:20 -0800
description: Markdown reference notes.
img: markdown.jpg
tags: [Markdown]
---
These are my Markdown Basics reference notes. Markdown was designed to be an
easy to write plain text formatting syntax for writers, inventors, and bloggers.

<p>Here's a link to download this example. <a href="https://github.com/johnnyromano/Markdown" alt="Markdown notes file on Johnny's Github">github.Markdown</a></p>
---
## Headlines, Paragraphs, and Basic Formatting

### Headlines

Type a single hash (AKA pound symbol) and a space to create the largest or first-level heading. A second-level heading uses two hashes next to each other followed by a space and text. The rest of the headline levels just add another hash.

```python
### Headline level 3

```

#### Heading Level 4

##### Heading Level 5

###### Heading Level 6

### Paragraphs and Line Breaks

#### Paragraphs

We create paragraphs by typing the way we would in any other program. Just hit return twice to start another paragraph.

Where you see empty space between blocks of text in your Markdown document, you will see empty space separating those blocks of text in your formatted HTML document.

#### Line Breaks

To create a line break after a line
but not a new paragraph you add two spaces
to the end of a Line
just like this

### Emphasis and Bolding

#### Italics

Emphasis can be added with either the asterisk or the underscore characters.
You can use \**asterisk*\* or \__underscore_\_

### Bolding

You can use double **\*\*asterisk\*\*** or double \____underscore\____

### Italics and Bolding

is done with ***triple asterisk***

### Blockquotes

A blockquote sets text apart from the rest of the document. It indicates that the text is quoted from another source.

You format a blockquote using the greater than symbol. If you want a blockquote to span multiple paragraphs, add the greater than symbol to the line between paragraphs too.

>hello how are you today?
>

### Horizontal Rule

---

___

***

## Lists

You can write both numbered and bulleted lists with Markdown.

### Numbered Lists

You create numbered lists like you do in other writing programs. Type the number, a period, a space, and the item label. To nest an item, indent it with a tab or at least two spaces beneath the item above it.

1. Item 1
  1. Nested Item 1
  2. Nested Item 2
    1. Nested even further Item2
2. Item 2

### Bulleted Lists

Bulleted lists work like numbered lists, but you use the asterisk character, a space, and no period. You can nest bulleted items too. We just indent our item below another item like we did with our numbered list.

* Item
* Another Item
  * Add two spaces of a tab
    * Yet another type of Bullet

### Mixed Lists

You can mix the two list styles too. Just use the numbers or asterisks where you want them.

1. Item One
  * Nested Item
  * Nested Item
2. Item two
  * Nested Item
  * Nested Item
    1. Deep Nested Item One
    2. Deep Nested Item two
      * Super Deep Nested Item
      * Super Deep Nested Item

### Task Lists

- [x] buy the eggs
- [x] buy the pancake mix
- [ ] eat the pancakes

---
## Fenced Code Blocks

We format code using the backtick character. The backtick is on the same key as the tilde on a U.S. English keyboard, which is usually to the left of the number 1 and above the tab key.

You can use a single backtick to create inline code. For example, you may type something like this:

To install the latest version of NPM, you can type, `npm install npm@latest -g`

For multiple lines of code, you'll usually create a code block. Instead of one backtick, use three backticks above and below the code block.

```JavaScript
let exampleFunction = () =>{
    let foo = 'foo';
    let bar = 'bar';

    return foo + bar;
}

```

```python
def user_status():
  user = 'johnny'
  msg = 'The user {} is working.'.format(user)

```
output:
`>>> The user johnny is working.`

---

## Tables

Name | Vehicle Type
-----|-------------
Dave | Truck
Steve | Car
Susan | Airplane

---


## EMOJI
[EMOJI Cheat Sheet](https://www.webpagefx.com/tools/emoji-cheat-sheet/ "A link to a ton of EMJOI")

:+1: :camel: :tada: :rocket: :metal: :octocat:
:sparkles: :collision: :bug: :honeybee: :seedling:


---
## Links

[visit jpromano.com](http://jpromano.com)

[add tool tip for weblink](http://jpromano.com "Amazing Guy")

[jpromano.com][1]

[1]: http://jpromano.com "Reference link to the amazing johnny romano"

---
## Images
Type a label for the image in square brackets. On the Web we call this alt text, because it will be displayed as an alternate if the image cannot be shown for any reason. I have an image of kittens, so I’ll write, “Kittens” in square brackets and follow that with the url for the image in parenthesis.

That creates a link for the kitten image, but I want to display the image. All I have to do is add an exclamation mark in front of the square brackets.

![Kittens](https://placekitten.com/250/400)
What if I want the image to link to something too? Just add square brackets around your whole image code. At the end of the new square brackets, put the link url in parenthesis.

[![Kittens](https://placekitten.com/300/400)](https://placekitten.com)

Images can have titles like links too. You add them the same way. After the image url, add a space and put the title in quotes.
![Kittens](https://placekitten.com/250/400 "Whaaa chu lookin at")

---
#### the end, for now...
