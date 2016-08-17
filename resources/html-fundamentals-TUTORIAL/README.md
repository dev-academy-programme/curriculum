# HTML fundamentals tutorial

## Overview
A detailed walkthrough of HTML

1. Learn the basics of HTML.
2. Get some familiarity with the HTML content categories and the elements in each.
3. Build a basic web page using proper HTML markup.

## Topics covered / Keywords
- basic elements
- semantic elements
- <!DOCTYPE html>

### Exercise

Create a folder called `html-fundamentals` in your git repo, and a file called `index.html` inside it.

In general, we will use folder names to indicate the page, and a file in the folder always called `index.html` to contain the HTML content for the page. The reason for this is that it allows the user to access the page without having to use a file extension. For example, in this case the URL would be `/html-fundamentals/`, not `html-fundamentals.html` or `html-fundamentals/index.html`.

This works because `index.html` is the name for the *default* web page in the folder, so the browser will grab it if no file name is given. The reason we want to hide the "html" extension is because it is "leaky". By that we means that it leaks details about our *implemenation* (that it's HTML) to the user. This is bad practice, or what you'll hear developers refer to as a "code smell". Not a good smell, either.

So create your `index.html` page, then use the MDN [HTML element reference](https://developer.mozilla.org/en-US/docs/Web/HTML/Element) to look up the meaning of the following HTML elements. Build a basic page using these elements (start with the minimum HTML below).

When you're done, commit your changes and push them to your repo so we can provide feedback on them.

Here are the HTML elements your page should include:

- Everything in the "minimum HTML" shown below.
- A `<link>` to the [Bootstrap CDN] in the `<head>` element just above the closing `</head>` tag.
- A `<header>` containing an `<h1>` element with the site name.
- A `<nav>` element with a few links to (fake) other site pages. If you like, you can enclose these in a `<ul>` and `<li>` elements. The links will use the `<a>` anchor element. Look them up!
- A `<main>` section containing two `<article>` elements, each with a `<header>` and `<h2>` element with the article title, and a couple `<p>` of text. Or get creative with `<img>`, `<table>`, or `<form>` elements. Have fun.
- A `<footer>` element with copyright information and links to a (fake) privacy policy and terms of use.

(For fake links you can just use `href="#"`.)

You can use the [W3C HTML validator](https://validator.w3.org/#validate_by_input) to make sure your HTML is correct *before* submitting your work to us. Right? Just copy and paste your HTML (all of it) into the handy form field and click the "Check" button for pleasant (?) surprise.

## Hypertext Markup Language fundamentals

### What do we mean by "semantic"?

**Semantic:** relating to meaning in language or logic.

With HTML, we mean that we use the language to mark up the content of the page with labels that add *meaning* to the content.

Sometimes this meaning is purely structural, for example, the `<p>` element is used to tell the user agent that the enclosed content is a paragraph:

```html
<p>This is a very short paragraph.</p>
```

If we view this in a browser, it will have a *default style* associated with it. In most cases, this will be that the paragraph is shown on it's own line or lines, and that there is a bit of space (margin or padding) above and below the paragraph to distinguish it from the surrounding content.

But this default style is not part of HTML! Style is added by CSS. So the real information provided by the `<p>` element is *only* that the content is a paragraph.

Consider that this paragraph might be read aloud by a screen reader, or parsed for keywords by some kind of software robot. Where is the margin, padding, line break then? Can you see that those have nothing to do with the *function* of this element?

Other HTML elements provide different kinds of meaning. Some examples:

- `<header>` is used for the header of a page *or a section of the page*. Note that "header" is used figuratively to mean the section that has key information about the page, such as the title, or about the site, such as the logo and name of the site. It does not have to appear at the top of the page or section visually to be a header, though usually that's where you'll find it.
- `<footer>` is the opposite of a header, of course. This is where you'll find less important information about the page or section. It is usually found at the foot&mdash;the bottom&mdash; of the page or section, but like the header, it is about *meaning*, not display, so it could also appear at the top or to the side.
- `<nav>` is used for navigation elements, such as global links.

And so on.

### What is this DOCTYPE thing?

At the top of each HTML page, you should find a DOCTYPE element. It's a special element and not part of the HTML. For all current pages, the DOCTYPE is quite simple:

```html
<!DOCTYPE html>
```

This is a processing instruction to the user agent (browser) that tells it how to parse (interpret) the HTML that follows. This particular DOCTYPE tag tells the browser that the HTML that follows is HTML version 5.

If you leave it off, some browsers may give you weird bugs. So use it and that's one less thing to worry about!

### What is the minimum HTML for a valid web page

Well, the truth is that this seems to change with every version of HTML, and with HTML5 it is something ridiculous. But who cares? What we really want to know is what is the minimum starting template for a *real* HTML page.

Here's a good one. You can make a [gist](https://gist.github.com/) of it on GitHub and use it as the basis for all your HTML pages.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>Page title (goes in the tab on the browser)</title>
  </head>
  <body>
  </body>
</html>
```

HTML elements are used to mark up content by putting HTML "tags" at the beginning and end of the content to be marked up. The start tag has the name of the HTML element in lowercase letters:

```html
<p>
```

And the end tag has the name preceded by a /:

```html
</p>
```

Some elements, such at the `<img>` element, which is used to embed an image in the web page, have no content (the image is linked, not enclosed). For "empty" elements such as this, you can leave off the closing tag. But for elements that expect content, such as the `<p>` element, you should always include the closing tag *even if there is no content*:

```html
<p></p>
```

### Elements have attributes

The name of the element is often not enough. Quite frequently, we'll want to associate other information with that element.

Sometimes this is nothing more than giving the element a "class" attribute so that we can apply special styles to it with CSS, or an "id" attribute so that we can get hold of it from our JavaScript to interact with it.

But there are many more attributes. For example, the element that links to other pages, which for historical reasons is the `<a>` element (not the `<link>` element&mdash;don't get them confused), needs the URL of the page to which it links. We add this with a "hypertext reference" attribute abbreviated *href*:

```html
<a href="https://google.com/">Google!</a>
```

Or, if we're creating a form, we'll want to tell it whether to submit the data via GET or POST, and what URL to submit it to. We use the *method* and *action* attributes, respectively, to provide that information:

```html
<form id="search" method="GET" action="/results">
  [form elements here]
</form>
```

### What HTML elements are available?

Oh, wow! There are many! Fortunately, most of them you'll rarely if ever use. So you can focus on the few key ones. We'll cover them in our deliverable today.

The kinds of HTML elements available are grouped into seven overlapping categories called "content categories". These are:

1. Metadata
2. Flow
3. Sectioning
4. Heading
5. Phrasing
6. Embedded
7. Interactive

You don't need to memorize this stuff! Just take a look at this excellent discussion about [content categories](https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/Content_categories) at the Mozilla Developer Network. MDN is the go-to resource for everything HTML (and CSS and JS). It's much easier to read than the standards, and is much more likely to be both up-to-date and correct when compared to most resources.

If you find MDN a bit difficult, read our [reading documentation concept](https://github.com/dev-academy-programme/curriculum/tree/master/concepts/reading-documentation). You're going to be using MDN a lot. The sooner you get comfortable with it, the better.

### Putting it all together

So now we have enough information to work through our minimum HTML document above. Let's take it piece by piece.

```html
<!DOCTYPE html>
```

This tells the browser that the content to follow is HTML version 5. It helps prevent buggy pages. Use it. It must be the *first* line in your HTML file.

```html
<html lang="en">
  [content here]
</html>
```

HTML is organized like boxes in boxes in boxes. It's important to make sure that a box that starts *inside* another box also *ends* inside that box. It doesn't make sense to have boxes overlapping. We call that "bad nesting".

The outermost box is the `<html>` element itself. The "lang" attribute sets the language of the *content* of this HTML document to English.

```html
<head>
  [invisible content here]
</head>
```

The `<head>` element contains "metadata"&mdash;that's data *about* the data (meta means "about"). This is information that, with the exception of the title, is invisible to the user. Here we provide metainformation such as the author, the character set (more on this later), the size of the viewport (ditto), links to stylesheets and script files, etc.

The opposite of the `<head>` is the `<body>`:

```html
<body>
  [visible content here]
</body>
```

The body is where we put the part of the page that the user sees. It's that simple. We can also put links to stylesheets, scripts, etc. here, and sometimes we do, but usually all of that is put in the `<head>`.

```html
<meta charset="utf-8">
```

This tells the user agent (browser) that the text in the file uses the UTF-8 character set. This is an international set of characters (letters, digits, punctuation, etc.) that includes pretty much every character in every alphabet in the world. So it can handle almost every human language and then some. We'll always use UTF-8, so just use it and don't worry too much. Just be glad that you came to web development *after* the character encoding wars ended. It was bloody.

```html
<meta http-equiv="X-UA-Compatible" content="IE=edge">
```

Internet Explorer (Microsoft's flagship browser) *sucks*. There, we've said it. For some reason, Microsoft apparently wants to torture all web developers for all eternity, so Internet Explorer (IE for short) has almost always been buggy and non-standards-compliant. This has made it the most widely-hated browser in Internet history (by web developers, that is). This tag fixes a problem with some IE versions. Sigh. Use it for now.

```html
<meta name="viewport" content="width=device-width, initial-scale=1">
```

Now that we have smart phones and tablets galore, we have to allow for the smaller size of their viewports. This tag is used to set the scale of our page. You'll learn more about it later. For now, this is a good start.

```html
<title>Page title (goes in the tab on the browser)</title>
```

Every page must have a title. This appears in the tab of the browser (or the browser window title bar, if no tabs are used). It also is used by many search engines, which makes what we put in it quite important. We'll talk more about this later.

And there's your tour of HTML. Now go back to the deliverables and give them a try.

## Resources

- [MDN HTML](https://developer.mozilla.org/en-US/docs/Web/Guide/HTML)
- [Content categories](https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/Content_categories)
- [HTML5](https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/HTML5)
- [HTML element reference](https://developer.mozilla.org/en-US/docs/Web/HTML/Element)
