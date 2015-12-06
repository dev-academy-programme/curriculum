# Validating your HTML

## Open HTML page locally
`cd` to the directory where your HTML file lives, and then start up the Python web server by typing this command in the terminal:

```js
python -m SimpleHTTPServer 3000
```

This will run a web server in that folder until you hit Control-c to stop it. It will tie up the terminal, so if you need a terminal for any reason while the web server is running, just open a new one from the dock.

This runs the server on port 3000, so you'll have to access it with `http://localhost:3000/` in the browser (see the image above).

Here's what the web server looks like when you start it up and request the page:

<figure>
  <img src="../images/python-web-server.png" alt="Web server"><br>
  <figcaption>
    <p><strong>Figure 2:</strong> The python web server</p>
  </figcaption>
</figure>

When you test your pages, you'll always want to run some kind of web server. The python server is easy and available, so why not. Just don't tell anyone we have you using Python!

## Check HTML generates document outline
We've installed the Document Outliner tool in Chrome, and it gives you a nice idea of the structure of your page. Check this out:

<figure>
  <img src="../images/document-outliner.png" alt="Document outliner"><br>
  <figcaption>
    <p><strong>Figure 3:</strong> The HTML5 Document Outliner at work</p>
  </figcaption>
</figure>

Just click on that outline icon to see it.

## Validate your HTML
Use the Web Developer Tools extension in Chrome:

<figure>
  <img src="../images/web-dev-tools.png" alt="Web developer tools"><br>
  <figcaption>
    <p><strong>Figure 4:</strong> Validate Local HTML in the Web Developer Tools tab</p>
  </figcaption>
</figure>

If you click on "Validate Local HTML", you should get this kind of output:

<figure>
  <img src="../images/validator-output.png" alt="No HTML errors"><br>
  <figcaption>
    <p><strong>Figure 5:</strong> Output of the W3C HTML validator</p>
  </figcaption>
</figure>

Now you know you're standards compliant!
