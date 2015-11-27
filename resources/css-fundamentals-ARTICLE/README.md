# CSS fundamentals

## Objectives

1. Learn how to use selectors to apply styles to HTML elements.
2. Get a basic idea of how CSS is organized.
3. Understand how the cascade works and what gets precedence.


## How to use
[Optional] Use this as a guide to add some stylin' to your blogs.

You can use MDN's wonderful [Getting started with CSS](https://developer.mozilla.org/en-US/docs/Web/Guide/CSS/Getting_started) reference.

## Cascading Style Sheets fundamentals

For the purposes of testing these ideas, we'll add our stylesheet right into our HTML using a `<style>` element:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>Page title (goes in the tab on the browser)</title>

    <style type="text/css" media="all">
      p {
        color: red;
      }
    </style>

  </head>
  <body>
    <p>This text should be red.</p>
  </body>
</html>
```

### Selectors

Before we can apply styling rules to our HTML elements, we need some way for our stylsheet to get hold of them. We do this by using a "selector".

There are many types of selectors and combinations of selectors, but for this sprint, we'll focus on just two of them.

#### Tag names

We can select an element to apply our style to by using the tag name of that element. For example, to turn the text in our paragraph elements to red, we could do this:

```css
p {
  color: red;
}
```

One unfortunate effect of this is that it turns the text in *every* `<p>` element on the page red. What if we wanted to apply the color change only to a small set of `<p>` elements?

Well, if we think of those elements as forming a "class", then we could use the class attribute to semantically label the paragraphs in that class, and then we could apply our CSS rules only to that class of paragraph.

#### Class names

For example, let's say we have paragraphs in special pull quote sections on our page, and we want to color them blue. We could add a "pull-quote" class to the `<p>` tags in our pull quotes:

```html
<div>
  <p class="pull-quote">First para . . .</p>
  <p class="pull-quote">Second para . . .</p>
</div>
```

Now we can apply our blue text color like this:

```css
p.pull-quote {
  color: blue;
}
```

That should work. The `.` indicates a class attribute, so this says "apply the rules inside the braces to every `<p>` element with the attribute `class` having the value `pull-quote`".

Do we really need the "p"? Probably not. We could just as easily apply the rule to *all* elements with a class of "pull-quote". But if we re-used that class elsewhere, we might want to have different rules for different elements, so be careful.

It's kind of annoying to have to add it to every paragraph. Is there a better way?

Well, we could always add it to the `<div>` that encloses the pull quotes instead:

```html
<div class="pull-quote">
  <p>First para . . .</p>
  <p>Second para . . .</p>
</div>
```

Now we have to change our CSS to reflect that the "pull-quote" class is on the *parent* element:

```css
.pull-quote p {
  color: blue;
}
```

Note the space between ".pull-quote" and "p". That's important! It means, "find any element with a class of 'pull-quote', and then look for every `<p>` element inside that element and apply the rules inside these braces to those elements".

#### Combinations

Suppose we wanted to designate one paragraph in our pull quote as the "key" paragraph and to show that one in italics. We could add a "key" class name to that paragraph, and apply the style like this:

```html
<div class="pull-quote">
  <p>First para . . .</p>
  <p class="key">Second para . . .</p>
</div>
```

```css
.pull-quote p { color: blue; }
.pull-quote .key { font-style: italic; }
```

So what happens to the second paragraph in the pull quote now? Is it blue? Is it italicized? Is it both? Try it and find out.


### Properties and values

There are a great many CSS properties. We can control font, position, text, borders, and much more.

The general pattern for CSS rules is `property: value;`. Note the colon and the semi-colon. These are not optional. It's property, colon, value, semicolon. In that order. Some people skip the space between the colon and the value, but we recommend against that. It will work fine right up until it doesn't, and then you'll pull your hair out trying to figure out why it's not working. And it's simply more readable, and readability is extremely important for code, which isn't that easy to read even when it's nicely formatted.

Some properties take an individual value, which may have units. For example, we can set the font-weight to bold like this:

```css
font-weight: bold;
```

Other properties allow us to combine multiple properties into one. For example, this:

```css
border-width: 1px;
border-style: solid;
border-color: gray;
```

Can be rewritten like this:

```css
border: 1px solid gray;
```

(Note that it's width, style, color here, though the order is not fixed.)

And margins (space around the element) can be written like this:

```css
margin-top: 5px;
margin-right: 10px;
margin-bottom: 15px;
margin-left: 0;
```

Or this:

```css
margin: 5px 10px 15px 0;
```

(Note that it's *always* top, right, bottom, left, in a clockwise rotation, and that values of 0 do not need units. Or we can just use a single value to specify all four margins at once.)

Look through the [MDN CSS reference](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference) to learn more. But don't memorize any more than you need to! Just bookmark the CSS reference and refer to it when you need to find out how to set something. If you use a property often enough to be worth memorizing, then you'll remember it anyway. If you don't remember it, then it's probably not worth your time to memorize it.

### The cascade

The "cascade" is fairly simple: if a rule comes after a similar rule, the latter rule overrides the first rule. So if I were to do this:

```css
p {
  margin: 20px;
  margin-bottom: 5px;
}
```

Then I would get a margin of 20px on all sides, after which I would override the bottom margin and set it to 5px. If I swap the order of these rules, I'll get 20px on all sides.

This applies to rules wherever they are. If I put CSS in one file and load it, then load CSS in another file, the CSS in the latter file can override that in the earlier file. At the bottom of all this is that I can declare the style right on the HTML element using the `style` attribute:

```html
<p style="color: red">This is red text.</p>
```

That said, you should almost never put your styles in the HTML itself (except briefly to test a rule). The reason is because we *want* to be able to override styles as necessary. Styles in the HTML itself are almost impossible to override without resorting to tricks.

Also, this sort of violates our separation of concerns. True, we're still using CSS, but by putting it right in the HTML, we have to add our CSS to each element individually, and it's right in the HTML. That costs us all the benefit of centralizing our CSS in a separate file which we can easily swap out when necessary.

For now, just write your CSS in the `<style>` element in the head of the HTML document. Later we'll put our CSS in a separate file and we'll link to it from our HTML.

### Validation!

Don't forget that you can validate your CSS to make sure it's correct. Should you? Of course you should. Every time. Make it a habit.

Use the [W3C CSS validator](https://jigsaw.w3.org/css-validator/#validate_by_input) and copy and paste your CSS in the big text box, then click the Check button to see the results.

## Further resources

- [MDN CSS](https://developer.mozilla.org/en-US/docs/Web/CSS)
- [MDN CSS reference](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference)
- [Getting started with CSS](https://developer.mozilla.org/en-US/docs/Web/Guide/CSS/Getting_started)
- [Selectors](https://developer.mozilla.org/en-US/docs/Web/Guide/CSS/Getting_Started/Selectors)
- [W3C CSS validator](https://jigsaw.w3.org/css-validator/#validate_by_input)
