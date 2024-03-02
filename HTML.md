# HTML
## Introduction
- **HTML** stands for Hyper Text Markup Language. HTML is the standard markup language for creating Web pages.
- HTML is the most basic building block of the Web.
- When the Web was born, we had HTML files, they were stored on a server (a centralized location), and browsers were able to visualize the content of the HTML files by asking them to the server.
- HTML not strictly a programming language. It is a markup language, and it is structured using tags.
- In an HTML file, we basically write text, as we would in a plain text file, but we save it with the .html file extension.
```html
<p>A paragraph of text</p>
<ul>
  <li>First item</li>
  <li>Second item</li>
  <li>Third item</li>
</ul>
```
- This HTML snippet says that A paragraph of text is a paragraph. And then we have a list of 3 items.
- p stands for paragraph, ul stands for unordered list, and li stands for list item.
- For each of them, we have an opening tag ```(like <p>)``` the content, and a closing tag ```(like </p>)```.
- So ```<opening tag> …content … </closing tag>```.
- You don’t tell "make this paragraph red" in HTML.That’s a presentational aspect.
- HTML is just concerned with content.
- It just adds some predefined styles here and there, like for example with the list. But that’s it. There’s no customization you can do on how it looks, in HTML.This will be the job of CSS.
## Your first HTML page 
Here’s a more correct version of that:
```html
<!DOCTYPE html>
<html>
  <head>

  </head>
  <body>
    <p>A paragraph of text</p>

    <ul>
      <li>First item</li>
      <li>Second item</li>
      <li>Third item</li>
    </ul>
  </body>
</html>
```
- The elements we had before are wrapped into the body tag.
- That, along with head (in this example empty), is contained in the html tag, which is the root tag.
- Body contains the visible elements of the page.
- Head is used to contain special information about the content and more, as we’ll see later.
- In a document, we can have only 1 appearance of html, body and head.
- Finally, at the top we have the doctype: ```<!DOCTYPE html>```. This tells the browser “this is an HTML file”.
- Nested tags should be indented.
- In the example, the ```ul``` tag contains the li tags, so li tags are nested.
- Use 2 or 4 characters, or the tab character to indent those nested elements, depending on your preference, but keep a “tree structure”. That will make it much easier to visually parse an HTML file.

## Text tags
### Inline and block elements
- Before looking at tags, we need to separate them into 2 categories: **block elements** and **inline elements**.
- Block elements (```p```,` div`, heading elements, lists and list items, and others) when positioned on the page do not allow other elements to be visualized next to them.
- Inline elements instead can sit next to other inline elements.
- Another difference is that inline elements can be contained in block elements. The reverse is not true.
### `p` and `span`
- The p tag defines a paragraph of text, and it’s a block element:
```html
<p>Some text</p>
```
- Inside a `p` tag, we can add any inline element we like, like `span`.
- The span tag is an inline tag:
```html
<p>A part of the text <span>and here another part</span></p>
```
- We cannot add other block elements into a `p` or `span` tag.
- We cannot nest a `p` element into another one, as `p` is a block tag.

## Heading tags (`h1`, `h2`…)
- HTML provides us with 6 heading tags.
- `h1`, `h2`, `h3`, `h4`, `h5`, `h6`
- Typically a page will have one `h1` element, which is the page title. Then you might have one or more `h2` elements depending on the page content.
- The browser by default will render the h1 tag bigger, and will make the elements size smaller as the number near h increases:
```html
<h1>h1</h1>
<h2>h2</h2>
<h3>h3</h3>
<h4>h4</h4>
<h5>h5</h5>
<h6>h6</h6>
<p>Paragraph</p>
```
- All headings are block elements. They cannot contain other tags, except tags that identify text such as `a` `span` or `strong`.

## Attributes
- The opening tag of an element can have special snippets of information we can attach, called attributes.
- Attributes have the `key="value"` syntax:
```html
<p class="a-class">A paragraph of text</p>
```
```html
<p class="a-class" id="an-id">A paragraph of text</p>
```
- some attributes are boolean, meaning you only need the key, for example, see the defer attribute on the script tag:
```html
<script defer src="file.js"></script>
```
- The `class` and `id` attributes are two of the most common you will find used.
- The difference between the two is that an `id` is unique in the context of a web page; it cannot be duplicated.
- Classes, on the other hand, can appear multiple times on multiple elements.
- an id is just one value. class can hold multiple values, separated by a space:
```html
<p class="a-class another-class">
  A paragraph of text
</p>
```
- Some attributes are only used for one tag, highly specialized. Others have more broad applications, like `id` and `class` you just saw.

## Links
- Links are defined using the `a` tag. The link destination is set via its `href` attribute.
```html
<a href="https://flaviocopes.com">
  click here
</a>
```
- The above example is an absolute URL. Links also work with relative URLs:
```html
<a href="/test">click here</a>
```
- In this case, when clicking the link the user is moved to the /test URL on the current origin.
- Be careful with the / character. If omitted, instead of starting from the origin, the browser will just add the test string to the current URL.
- Link tags can include other things inside them, not just text. For example, images can be links, too, so you click an image and you open a new page.

## Images
- Images can be displayed using the `img` tag.
- This tag accepts a src attribute, which we use to set the image source:
```html
<img src="image.png" />
```
- Note that this is a self-closing tag (ends with `/>`), it does not contain any content - it’s self-sustaining.
- The HTML standard requires an alt attribute to be present, to describe the image. This is used by screen readers and also by search engine bots:
```html
<img src="dog.png" alt="A picture of a dog" />
```
- You can set the `width` and `height` attributes to set the space that the element will take so that the browser can account for it and does not change the layout when it’s fully loaded. It takes a numeric value, expressed in pixels.
```html
<img src="dog.png" alt="A picture of a dog" width="300" height="200" />
```

## Lists
- We have 2 main kinds of lists: **unordered** lists and **ordered** lists
-  Unordered lists are created using the `ul` tag. Each item in the list is created with the `li` tag:
 ```html
 <ul>
  <li>First</li>
  <li>Second</li>
</ul>
```
- Ordered lists are similar, just made with the ol tag:
```html
<ol>
  <li>First</li>
  <li>Second</li>
</ol>
```
- The difference between the two is that ordered lists have a number before each item.

## Head tags
- The `head` tag contains special tags that define the document properties.
- It’s always written before the `body` tag, right after the opening `html` tag:
```html
<!DOCTYPE html>
<html>
  <head>
    ...
  </head>
  ...
</html>
```
- We never use attributes on this tag.
- And we don’t write content in it.
- It’s just a container for other tags.
- Inside it we can have a wide variety of tags, depending on what you need to do:
  - `title`
  - `script`
  - `link`
  - `style`
  - `meta`

## Container tags
- HTML provides us with some tags we can use to group other tags together.
- Suppose you want to group together a `<p></p>` and an `<img />`.
- You can use <div></div>.
```html
<div>
  <p>hello!</p>
  <img src="test.jpg" alt="an image" />
</div>
```
- `div` is the generic container element:
```html
<div>
	...
</div>
```
- It’s the one we use when we don’t have another dedicated container tag like article.
- We often add a class or id attribute to this element, to allow it to be styled using CSS.
- Other container tags are called semantic elements :
  - `section`
  - `article`
  - `header`
  - `aside`
  - `main`
  - `footer`
  - `nav`
- They do not have any special style applied, they all work like `div` but their name has a specific meaning attached.
```html
<div>
  <div class="header">
    <h1>Title</h1>
  </div>
  <div class="article">
    <p>Article content</p>
  </div>
  <div class="footer">
    <p>Some footer info</p>
  </div>
</div>
```
- Or you can give those sections more meaning in this way, without using class attributes:
```html
<section>
  <header>
    <h1>Title</h1>
  </header>
  <article>
    <p>Article content</p>
  </article>
  <footer>
    <p>Some footer info</p>
  </footer>
</section>
```
- Nothing changes from the visual point of view. But those tags have more meaning, and tools like screen readers can infer information from this meaning.
### `article`
- The article tag identifies a thing that can be independent from other things in a page.
```html
<article>
	<h2>A blog post</h2>
	<a href="/1">Read more</a>
</article>
<article>
	<h2>Another blog post</h2>
	<a href="/2">Read more</a>
</article>
```
- An article can also be the main element in a page.
```html
<article>
	<h2>A blog post</h2>
	<p>Here is the content...</p>
</article>
```
### `section`
- Represents a section of a long article. Each section has a heading tag (`h1`-`h6`), then the  section content.
```html
<article>
	<section>
		<h2>A section of the page</h2>
		<p>...</p>
		<img ...>
	</section>
	<section>
		<h2>Another section of the page</h2>
		<p>...</p>
	</section>
</article>
```
- This tag is useful to break a long article into different sections.
### `nav`
- This tag is used to create the markup that defines the page navigation. Into this we typically add an ul or ol list:
```html
<nav>
	<ol>
		<li><a href="/">Home</a></li>
		<li><a href="/blog">Blog</a></li>
	</ol>
</nav>
```
### `aside`
- The `aside` tag is used to add a piece of content that is related to the main content.
- A box where to add a quote
```html
<div>
  <p>some text..</p>
  <aside>
    <p>A quote..</p>
  </aside>
  <p>other text...</p>
</div>
```
Using `aside` is a signal that the things it contains are not part of the regular flow of the section it lives into.
### `header`
- The `header` tag represents a part of the page that is the introduction. It can for example contain one or more heading tag (`h1`-`h6`), the tagline for the article, an image.
```html
<article>
  <header>
	  <h1>Article title</h1>
  </header>
  ...
</article>
```
### `main`
- The main tag represents the main part of a page:
```html
<body>
  ....
  <main>
    <p>....</p>
  </main>
</body>
```
### `footer`
- The `footer` tag is used to determine the footer of an article, or the footer of the page:
```html
<article>
 ....
  <footer>
    <p>Footer notes..</p>
  </footer>
</article>
```







