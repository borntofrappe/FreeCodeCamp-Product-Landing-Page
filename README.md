# The task

Complete the aptly named project in the line of "Applied Responsive Web Design Projects": *Build a Product Landing Page*.

Portion of the Responsive Web Design Section of the Beta Curriculum [@FreeCodeCamp](https://beta.freecodecamp.org).

---

The task itself comes accompanied by a considerable amount of requests. 

#### The page should have:

- a `<header>` element with `id="header"`; this portion should itself nest:

  - an image with `id="header-img"`;

  - a `<nav>` element with `id="nav-bar"`; which itself should be home to at least three click-able elements with `class="nav-link"`, directing each toward the respective section of the page.

- a `<video>` element with `id="video"`;

- a `<form>` element with `id="form"`; element which consists of:
  
  - an `<input>` field with `id="email"`, to submit email addresses;
  
  - a submut `<input>` with `id="submit"`, directing toward this static page: *https://www.freecodecamp.com/email-submit*

#### The layout of the page should also:

- incorporate a navbar always at the top of the viewport;

- make use of at least one media query and one flex container.

Beyond this, the actual design of the page and content of the different sections is free to be completed as wanted.
Even if not required, this is where a bit of extra effort and imagination are added.


# Lessons learned 

## A little planning goes a long way 

With the incorporation of plugins like [*Emmet*](https://emmet.io/) and tools like [*SASS*](http://sass-lang.com/), every project starts off with an exciting beginning. It is almost too easy to churn out HTML element and pile up many properties found in CSS. It is a thrilling sensation, albeit not a sustainable one.

I found a simple solution to this slightly taxing issue in simply sketching the layout of the page. While at first I would accomplish such a task with an image editor, the tool does very little in making the process more efficient. An equal amount of time can be spent in the design of a perfect mockup. Mockup almost impossible to be recreated in the web page with the same flair and sharpness, which only increases frustration in the methodology.

A far more simple and yet better alternative is just pencil and paper. Literlally though, not a tool named *pencil and paper*. You don't have to be an artist to draw boxes, and that is all the HTML sets out to build. 

I find the incorporation of this simple, preparatory phase to be incredibly valuable afterwards. Emmet abbreviations, SASS nesting, variables and all other helpful tools can then fall in the right places with precision and with purpose.

## Flex flex flex

Flex properties are used all throughout the document to lay elements in rows, columns and to align items in their respective containers.

One peculiarity of the current project is that flex items are also attributed the property of `display` set to `flex`, making them flex containers as well.

This nested structure is created to benefit from the advantages of flex properties in multiple layers.

```CSS
div {
  display:flex;
  ul {
    display: flex; <!-- flex item AND flex container-->
  }
}
```

In the small example, the unordered list is both a flex item and a flex container. It is therefore possible to lay and align the `ul` element inside of the wrapping `div` AND lay and align its nested items in the same way.

## SVG Set

SVG assets are defined in the HTML document, right in the beginning of the `<body>` tags, and later used as needed.

This separation of declaration and use is implemented in two steps, through the `<defs>` and `<use>` tags.

1. Declare SVG assets: **defs**

  In between `<svg>` tags, include all items you require inside of `<defs>` tags.

  In the wrapping tags, also set the property of `display` to `none` for the wrapping `<svg>` element. This to prevent the HTML from preemptively occupying space in the page.

  ```HTML
  <svg style="display:none;">
    <defs>
      <!--
      all SVG files, one at a time
      -->
    </defs>
  </svg>
  ```

  Be warned: for the wrapping tags, such as for group tags `<g>`, it is necessary to also specify the `viewbox` attribute. This will allow the SVG image to occupy the space it only requires and show the entire image without cropping (each SVG file should contain this element in the opening tag; simply copy paste the values in each of the SVG declaration).

  Beyond that, the inclusion of an `id` is advisable. This will be essential in targeting the particular SVG later in the page.

  ```HTML
  <svg style="display:none;">
    <defs>
      <g id="svg-id-one" viewBox="0 0 50 50">
       <!-- components of the SVG -->
      </g>

      <g id="svg-id-two" viewBox="0 0 50 50">
       <!-- components of the SVG -->
      </g>

      <g id="svg-id-three" viewBox="0 0 100 100">
       <!-- components of the SVG -->
      </g>
    </defs>
  </svg>
  ```

2. Use SVG files as needed: **use**

  Once declared at the top of the body, any SVG file can be included in the page through the `<use>` tags.

  Simply include the `<use>` tags in an `<svg>` element.  `<use>` tags with an attribute of `xlink:href`, targeting the declared SVG.

  ```HTML
  <svg>
    <use xlink:href="#svg-id-one"></use>
  </svg>
  ```

  Be warned: just be sure to include the attribute of `viewbox` with the same values with which the SVG was declared.

  ```HTML
  <svg viewBox="0 0 26.458 26.458">
    <use xlink:href="#product-icon"></use>
  </svg>
  ```


With this practice, which seems overly complicated , especially for just a single SVG, it is possible to implement SVG elements in a shorter format.

With additional items, the advantages are more evident: all declarations are grouped together in a single block of code and each SVG is used as needed throughout the page.

Once implemented, every SVG can be easily targeted in CSS, just like any HTML element, and styled accordingly.
