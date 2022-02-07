---
layout: post
title:  "Semantic HTML"
author: patrick
categories: [Web, HTML]
image: assets/images/semantic-html.jpg
beforetoc: "HTML (HyperText Markup Language) is the most basic building block of the Web"
toc: true
---

HTML is the standard markup language for Web pages. With HTML you can create your own Website.

HTML (HyperText Markup Language) is the most basic building block of the Web. It defines the meaning and structure of web content. Other technologies besides HTML are generally used to describe a web page's appearance/presentation (CSS) or functionality/behavior (JavaScript).

## What I Learnt from the Practical Course

### I was able to answer questions like

* What is HTML?
* What are tags & headers?
* How do you add lists, images, and links to your HTML page?
* What is a Pull Request?
* How do you use GitHub Pages?

I was able to:

* Make a simple HTML website
* Use foundational HTML concepts, like tags, headers, lists, images, and links
* Introduce changes with Pull Requests
* Deploy a web page to GitHub pages

**What I built?**
I built a simple [webpage](https://dev-path.github.io/intro-html/)

## Diging Deeper

### Understanding Articles and Section

*article* is another one of the new HTML5 elements that add semantic meaning to your markup. *article* is a sectioning element and is used to wrap independent, self-contained content. The tag works well with blog entries, forum posts, or news articles.

Determining whether content can stand alone is usually a judgment call, but you can use a couple of simple tests. Ask yourself if you removed all surrounding context, would that content still make sense? Similarly, for text, would the content hold up if it were in an RSS feed?

Remember that folks using assistive technologies rely on organized, semantically meaningful markup to better understand your work.

Note: The section element is also new with HTML5, and has a slightly different semantic meaning than article. An article is for standalone content, and a section is for grouping thematically related content. They can be used within each other, as needed. For example, if a book is the article, then each chapter is a section. When there's no relationship between groups of content, then use a div.

```html
<div> - groups content <section> - groups related content <article> - groups independent, self-contained content
```

### Using the Audio Element

HTML5's audio element gives semantic meaning when it wraps sound or audio stream content in your markup. Audio content also needs a text alternative to be accessible to people who are deaf or hard of hearing. This can be done with nearby text on the page or a link to a transcript.

The audio tag supports the controls attribute. This shows the browser default play, pause, and other controls, and supports keyboard functionality. This is a boolean attribute, meaning it doesn't need a value, its presence on the tag turns the setting on.

Here's an example:

```html
<audio id="meowClip" controls>
  <source src="audio/meow.mp3" type="audio/mpeg">
  <source src="audio/meow.ogg" type="audio/ogg">
</audio>
```

### Figure and Figcaption

HTML5 introduced the figure element and the related figcaption. Used together, these items wrap a visual representation (like an image, diagram, or chart) along with its caption. Wrapping these elements together gives a two-fold accessibility boost by semantically grouping related content and providing a text alternative explaining the figure.

For data visualizations like charts, the caption can be used to briefly note the trends or conclusions for users with visual impairments. Another challenge covers how to move a table version of the chart's data off-screen (using CSS) for screen reader users.

Here's an example - note that the figcaption goes inside the figure tags and can be combined with other elements:

```html
<figure>
  <img src="roundhouseDestruction.jpeg" alt="Photo of Camper Cat executing a roundhouse kick">
  <br>
  <figcaption>
    Master Camper Cat demonstrates proper form of a roundhouse kick.
  </figcaption>
</figure>
```

### Working with Radio Buttons

 Since radio buttons often come in a group where the user must choose one, there's a way to semantically show the choices are part of a set.

The fieldset tag surrounds the entire grouping of radio buttons to achieve this. It often uses a legend tag to provide a description for the grouping, which screen readers read for each choice in the fieldset element.

The fieldset wrapper and legend tag are not necessary when the choices are self-explanatory, like a gender selection. Using a label with the for attribute for each radio button is sufficient.

Here's an example:

```html
<form>
  <fieldset>
    <legend>Choose one of these three items:</legend>
    <input id="one" type="radio" name="items" value="one">
    <label for="one">Choice One</label><br>
    <input id="two" type="radio" name="items" value="two">
    <label for="two">Choice Two</label><br>
    <input id="three" type="radio" name="items" value="three">
    <label for="three">Choice Three</label>
  </fieldset>
</form>
```

### Date and Time

HTML5 also introduced the time element along with a datetime attribute to standardize times. The time element is an inline element that can wrap a date or time on a page. A datetime attribute holds a valid format of that date. This is the value accessed by assistive devices. It helps avoid confusion by stating a standardized version of a time, even if it's informally or colloquially written in the text.

Here's an example:

```html
<p>Master Camper Cat officiated the cage match between Goro and Scorpion <time datetime="2013-02-13">last Wednesday</time>, which ended in a draw.</p>
```

### Accessibility with CSS

CSS's magic can also improve accessibility on your page when you want to visually hide content meant only for screen readers. This happens when information is in a visual format (like a chart), but screen reader users need an alternative presentation (like a table) to access the data. CSS is used to position the screen reader-only elements off the visual area of the browser window.

Here's an example of the CSS rules that accomplish this:

```css
.sr-only {
  position: absolute;
  left: -10000px;
  width: 1px;
  height: 1px;
  top: auto;
  overflow: hidden;
}
```

Note: The following CSS approaches will NOT do the same thing:

display: none; or visibility: hidden; hides content for everyone, including screen reader users
Zero values for pixel sizes, such as width: 0px; height: 0px; removes that element from the flow of your document, meaning screen readers will ignore it.

### Accessibility with acesskeys

HTML offers the accesskey attribute to specify a shortcut key to activate or bring focus to an element. Adding an accesskey attribute can make navigation more efficient for keyboard-only users.

HTML5 allows this attribute to be used on any element, but it's particularly useful when it's used with interactive ones. This includes links, buttons, and form controls.

Here's an example:

```html
<button accesskey="b">Important Button</button>
```
