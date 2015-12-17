# ARIA roles

## Objectives

1. Get a basic idea of what ARIA is and why it's important.
2. Learn the "landmark" ARIA roles and how to use them.

## ARIA Roles Introduction

ARIA stands for Accessible Rich Internet Applications. It's a standard for making RIAs (the sorts of things you'll build as a web developer) more accessible to persons with disabilities.

One way that ARIA helps is by adding *semantic* (meaning) information to HTML elements. In other words, ARIA helps the browser or other "user agent" to understand the *function* of what's on the page&mdash;this is a banner, that's a search form, that other thing is the main content, and so on.

For an excellent (and brief) introduction to ARIA Landmark Roles, read Lyza Gardner's [WAI-finding with ARIA Landmark Roles](http://alistapart.com/column/wai-finding-with-aria-landmark-roles). You'll also find some good examples at this [HTML5 Accessibility](https://dequeuniversity.com/assets/html/jquery-summit/html5/slides/landmarks.html) page from dequeUniversity.

Here are a couple of examples for you:

Suppose that a `div` element is used to hold the main content of the page. HTML does provide a `<main>` element, but this is not standardized yet and not all browsers support it. Until then, we can alert accessibility devices that this is the main content on the page by adding the "main" role to the `<div>` tag:

```html
<div role="main">
  [main content here]
</div>
```

Similarly, if an element contains page navigation links, perhaps in a list element (`<ol>` or `<ul>`), then we might add the "navigation" role.

Here are the key ARIA landmark roles:

<dl>
  <dt>main</dt>
  <dd>
    The main content of the document. Typically following the navigation regions.
  </dd>
  <dt>navigation</dt>
  <dd>
    A collection of navigational elements.  Example: a left navigation area.
  </dd>
  <dt>search</dt>
  <dd>
    A region that contains a search widget.
  </dd>
  <dt>banner</dt>
  <dd>
    A region of site specific content, such as the identity of the site sponsor, etc.
  </dd>
  <dt>complementary</dt>
  <dd>
    A supporting section of the document, designed to be complementary to the main content. Example: Sports News and Business News on a typical news page. It should be meaningful when separated from the main content
  </dd>
  <dt>contentinfo</dt>
  <dd>
    A large region that contains information about the parent document. Example: footer of copyrights and links to privacy statements.
  </dd>
  <dt>form</dt>
  <dd>
    A region of the document that represents a collection of form elements. (In  HTML the HTML form element  can be used instead). Note: you should use the search role and not the generic form role for search forms.
  </dd>
</dl>

There are other roles, but these are a good start.

