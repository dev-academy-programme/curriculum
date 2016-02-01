<!-- DBC start -->
# Racer Game

## Learning Competencies

* Understanding events and callbacks in JavaScript
* Traverse and alter the DOM using JavaScript
* Write custom event handlers in JavaScript
* Build a pure JavaScript application

## Summary

Let's build a simple [drag race](https://www.google.co.nz/imgres?imgurl=http://i.imgur.com/lxV6GYl.gif&imgrefurl=https://www.reddit.com/r/funny/comments/195k3m/they_lost_against_dogs_xpost_rgifs/&h=184&w=450&tbnid=syPUFcJs2ph-wM:&docid=XOovZq3mwW4eBM&ei=Yy5zVq6hCIGzmAW4uKDYCw&tbm=isch&ved=0ahUKEwju3sC08OPJAhWBGaYKHTgcCLsQMwggKAYwBg) game with Javascript, HTML and CSS.

Each player will advance their "car" by smashing some key.  For example, player 1 might be the "q" key and player 2 might be the "p" key.

The goal here is to learn more about JavaScript, the DOM, and asynchronous
event handling.

You should have at least three files: an HTML file, a CSS file, and a JavaScript file. You can have more files, but all CSS and JavaScript should be linked externally from the HTML file.

## Releases

### Release 0: The Setup

There is no skeleton for this challenge.  You will have to write the HTML, CSS and
JavaScript files yourself (and link them all together).  Let's just start with
building a simple two-player board.  This will be rendered via HTML.  There are
a few ways you could do it, e.g., a table that looks like:

```html
<table class="racer_table">
  <tr id="player1_strip">
    <td></td>
    <td class="active"></td>
    <td></td>
    <td></td>
    ... etc ...
  </tr>
  <tr id="player2_strip">
    <td></td>
    <td></td>
    <td></td>
    <td class="active"></td>
    ... etc ...
  </tr>
</table>
```

Then, using CSS, you can provide styles like:

```css
.racer_table td {
  background-color: white;
  height: 20px;
  width: 20px;
}

.racer_table td.active {
  background-color: black;
}
```

Updating a player's position could be achieved by adding the `active` class to
the appropriate `td`.  There are many other ways to achieve a sensible board
output; this is just one suggestion.

Make sure you're able to "manually" produce all the board layouts you might
care about before you jump into the JavaScript.  Whatever way you choose, it
should be easy for JavaScript to manipulate, so keep that in mind.

Use something like [normalize.css][] to enable sane default styles.

### Release 1: Add JavaScript

How is your JavaScript going to talk to your to HTML? Use 'vanilla' JavaScript such as:
[.querySelector()][], [.querySelectorAll()][], and [.addEventListener()][] for traversing the DOM. 

We need some way for JavaScript to update the board state.  Create a simple
JavaScript function that can advance a particular player's position by one each time their key is pressed. You
give
the function a player as input and it will update the underlying HTML to
reflect the new position.

It could look something like:

```javascript
updatePlayerPosition('player1');
```

Store this JavaScript in a separate file and use the JavaScript console to
debug it and pass in values manually.



### Release 2: Binding to Key Presses

Now we'll make the game interactive!  Bind to the keyup event to detect
when a player has "pressed" a key.  We don't bind to the keydown or
keypress events because those events fire when the keyboard repeats the
key, whereas the keyup event doesn't.

It'd be a boring game if you could just hold the key and go.  You want to bind
to the `document`, like so:

vanilla javascript: 

```javascript
  document.addEventListener('keyup', someFunction, false)
```
Don't forget to only run the JavaScript after the page has loaded everything!  
We can do this with vanilla JavaScript:

```javascript
document.addEventListener('DOMContentLoaded', function() {
  //run the code
})
```


### Release 3: Starting and Winning States

Now that you have a functioning game, its time to add some more features. You
need to store starting and winning states so we can restart the game, declare a
winner, and turn off the keyboard event listeners.

Up until now, we've been using the DOM to store state in the form of HTML. But
JavaScript memory can be used to store state as well, as long as the user remains
on the page.

### Release 4: Dynamic Games

In release 0, we had you hard code the length of the game as table data cells. But
what if the game changed based on a variable set at the top of your JavaScript
file? like this:

```javascript
var lengthOfTrack = 30
```

Your task is to dynamically create the board based on that value. If you're feeling
adventurous, try to dynamically set the number of available players as well.

### Release 5: Think of Fun Additions

As a thought experiment, think about what would make this game more fun? Powerups? Landmines that send you back to the start? More player control?

Is your code well-suited to adding these features or would it be difficult?

How else could you build the game, perhaps without using a table?

## Resources

- [Mozilla documentation for: keyup](https://developer.mozilla.org/en-US/docs/Web/Reference/Events/keyup)
- [Mozilla documentation for: keydown](https://developer.mozilla.org/en-US/docs/Web/Reference/Events/keydown)
- [Mozilla documentation for: keypress](https://developer.mozilla.org/en-US/docs/Web/Reference/Events/keypress)

[.addEventListener()]: https://developer.mozilla.org/en-US/docs/Web/API/EventTarget.addEventListener
[.querySelector()]: https://developer.mozilla.org/en-US/docs/Web/API/document.querySelector
[.querySelectorAll()]: https://developer.mozilla.org/en-US/docs/Web/API/Document.querySelectorAll
[Racer]: ../../../racer-1-outrageous-fortune-challenge
[normalize.css]: http://necolas.github.com/normalize.css/
[Object literal notation]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Working_with_Objects
[Prototype-based OO]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Details_of_the_Object_Model
[Jasmine]: http://jasmine.github.io/2.0/introduction.html
<!-- DBC end -->
