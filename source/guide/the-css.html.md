---
title: The CSS
---

## CSS is easy, but develop scalable projects is something hard!

CSS, *Cascading Style Sheets* is one of the most complex and important parts of an web interface. Is through CSS that we can reach a project design, usually with not to much effort. You may wonder: *"Why CSS is a complex thing?"* and I will explain.

Since CSS never come up with exceptions, we usually underestimate it's complexity. In this days there are lots of large applications that need a complex CSS architecture to provide scalability, mainly when large teams are involved.

CSS is a flexible language and because of that you can write it in several ways and the final rendering will be the same. For example, the code bellow will have the same rendering by the browser.

```css
/*
 * Wow, what a horrible code!
 */
table.hl {
margin: 2em 0; }

    table.hl td.ln {
    text-align: right;
}

li { font-family: serif;
font-weight: bold;
    font-size: 1.2em;
}

/*
 * No things are getting better.
 */
table.hl {
  margin: 2em 0;
}

table.hl td.ln {
  text-align: right;
}

li {
  font-family: serif;
  font-weight: bold;
  font-size: 1.2em;
}
```

Now stop what you're doing and think. Do you even realize that sometimes you can have a CSS file with thousands and thousands of line that doesn't follow any standart?

There are a bunch of other issues with this language. Based on that you already realized that we have a long way to go.

## Basic Rules

### Selectors

As we said in [semantics page](/guide/the-semantic.html), without HTML there's no web and CSS is fully related to HTML tags. The main purpose of CSS is provide "styles" to our webpage and it uses the page elements to do that. For example:

```html
<a href="#">Links on the web should be red! Just kidding...</a>
```

```css
a {
  color: red;
}
```

The code bellow will apply a red color to all `<a>` tags in the document but not only HTML tags can be customized using CSS. Here there are some other selectors that can be used:

**Type selector**

HTML tags are type selectors, this means that, when in CSS, the selector of an tag `<p>` is simply `p` as well as the selector of a tag `<div>` is `div`.

**Class selector**

This will be the type of selectors that you will use more times during your development of stylesheets. In the HTML code the `class` attribute is associated to a tag so we can identify it. To set styles to this selector, in your css file, you will use the value of the `class` attribute preceded by a dot. Hard to understand? Let me draw it. I mean, code it to you...

```html
<div class="banner"></div>
```

```css
.banner {
  background: white;
  color: black;
}
```

**ID selector**

The `id` selector works the same way that `class` selector. It is created through the `id` attribute in a HTML tag. Right now you're probably asking yourself: *What is the difference between `id` and `class`?*

The difference between `id` and `class` selectors is that the first is more specific and less flexible. Based on it you should (almost always) use `class` when writing your code.

**Attribute selector**

There are a lot of attributes selectors. They are related to all elements that are able to have an attribute that may or may not have a value. For example, if you want to add a custom style to links that will open in a new window, do the follow:

```css
a[target="_blank"] {
  color: green;
}
```

**Pseudo-class selector**

Usually pseudo-classes selectors are used to refer to an element that is in a specific state, or in a position of a collection. The most common used are `:focus`, `:hover`, `:checked`, `:first-child` and `:last-child`.

It's easy to use them:

```css
/*
The code below will turn the link
color to green when the user hover
the cursor on it
*/

a:hover {
  color: green;
}
```

There are tons of pseudo-class selectors and you can take a better look in the [MDN list of selectors](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes).

**Pseudo-element selector**

With a very similar syntax of pseudo-class selectors, the pseudo-elements selectors insert a new node in the DOM, "simulating" an element.

Here a list of those selectors:

- `::after`
- `::before`
- `::first-letter`
- `::first-line`
- `::selection`
- `::backdrop`

**Combinators**

Like the name says, combinators are selectors that combine two or more elements. Here they are:

- Adjacent sibling selectors `el + el`
- General sibling selectors `el ~ el`
- Child selectors `el > p`
- Descendant selectors `el p`

**Universal selector**

A universal selector works in a global way. It apply the rules defined to it to all elements of the page.

```css
/*
This rule say that all
elements in the page
will be `display: block`.
*/

* {
  display: block
}
```

### Properties and values

If you're a programmer you can do a simple analogy. Think in the selectors as variables, properties are their attributes and these have a value. You got it?

Each selector have at least one property and its value. To understand it better we will divide properties in three different sections: positioning, box-model and fonts.

#### Position

On the web there are some different ways to position an element based in X, Y and Z axis.

The main property to do that is `position`. By using it we can choose how the element will be positioned in its container.

By default all elements have a static position, `position: static`, it means that its position in the page is based on the box-model (height, width, border, margin and padding).

Other commonly used value to this property is the relative position. Set an element as `position: relative` means that nothing will change at first but because of it you're now able to move your element around using `top`, `right`, `bottom`, `left` and move it in the Z axis using the `z-index` property. All those attributes can be used in combination with another position value, the absolute positioning. The big difference between `position: relative` and `position: absolute` is caused because when you have an absolute position set, the coordinates are now related to the parent element, not to the box-model anymore.

At last we can position an element fixed in the document using `position: fixed`. This way the element will be fixated in the screen based on the `<body>` dimensions.

#### Box-model

During your development time you will hear alot about **every element** be a "box". Therefore you need to know the properties that interfere in the dimensions of the box-model:

- `display`
- `height`
- `width`
- `margin`
- `border`
- `padding`
- `content`

Since the properties names are pretty intuitive we're not going to explain in details what each of one does.

#### Fonts

There are not many properties to handle with fonts in CSS. The main ones used are:

- `font-weight`
- `font-style`,
- `font-family`
- `font-size`
- `line-height`

## CSS3

In a few words, **CSS3 revolutionized** the way that we work with web interfaces, mainly when we're speaking about development productivity and application performance.

CSS3 allow developers to use less design tools to export images, that reduces the amount of files that are used to build the interface. Shadows, gradients, custom borders and fonts now work natively in newest browsers. This change causes a significant reduction of assets used, consequently there are less requisitions and it turns in a performance gain.

To learn more about it check [the MDN CSS3 page](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS3).

## Preprocessors

Good developers are always restless and they never are totally happy with the available solutions. Because of it there are always someone improving or *hacking* some language to make it better

Even with all improvements available in CSS3 the language still have limitations and to fill this lack some compiled languages were developed to work with CSS.

Nowadays the main ones are [Sass](http://sass-lang.com/) and [Less](http://lesscss.org/). Here some of the characteristics of them.

**Variables**

If you already work with CSS you know that it is a extremely repetitive language and this characteristic reduces the productivity of the developer. Luckily Sass and Less bring to us a few ways to resolve it. Variables is one of them.

```scss
// Scss (Sass)
$base-color: black;

body { color: $base-color; }
```

```less
// Less
@base-color: black;

body { color: @base-color; }
```

**Nesting**

Apply styles to elements that belong to the same parent element make us repeat a lot of code in CSS. When working with preprocessors we can use *nesting* and resolve that. However be careful with it, since is not recommended to use more than three levels of *nesting*.

In this case, both languages have the same syntax:

```scss
// Scss e Less
#header {
  a { color: blue; }

  p { color: black; }
}
```

**Mixins**

Like the name says, *mixins* "mix"  something in a rule. I help developers to reuse code. important to notice that if you need, is possible to add parameters to a mixin.

```scss
// Scss
@mixin border-radius(value) {
  -webkit-border-radius: value;
     -moz-border-radius: value;
          border-radius: value;
}

// To use the mixin above:
div {
  @include border-radius(3px);
}
```

```less
// Less
.border-radius(@value) {
  -webkit-border-radius: @value;
     -moz-border-radius: @value;
          border-radius: @value;
}

// To use the mixin above:
div {
  .border-radius(3px);
}
```

There are other similar features in both languages but mostly in Sass that have control structures, conditionals and functions.

## CSS architecture

Web applications are growing a lot in last years and because of that we need to improve the way that we write CSS. Now is necessary to think about scalability, code reuse, code standards to large teams, etc. This way is easier maintain the code in a long term application.

Because of this new worries some interesting paradigms like OOCSS, SMACSS and BEM have emerged and this is what we gonna see below.

### OOCSS

Created by [Nicole Sullivan](http://www.stubbornella.org), OOCSS means *Object Oriented CSS*.

This approach define that the classes need to be named based in their visual standart and not in its content. More than that, it suggests to create code to scrutctural objects without color proprieties like `background` or `color`. According with the OOCSS we need to set those color definitions in their particular classes. For example:

```css
alert {
  font-weight: bold;
}

alert-danger {
  color: red;
}
```

### SMACSS

SMACSS, *Scalable and Modular Architeture for CSS* is an approach created by John Snook to fix architectural problems from Yahoo mail. SMACSS code is based in five main cagetories: *base*, *layout*, *module*, *state* e o opcional *theme*.

The *base* stylesheet must have only rules of global selectors like `body`, `p`, `a`, etc.

In *layout* sheet SMACSS recommend you to put major layout styles, things like `header`, `article` and `footer`. Important to remember that the author recommend to use the `.l-` prefix to classes in this file.

The *module* file is destined to hold all elements that are components of the application. According to SMACSS, a good a practice to work with component is avoid element selectors. For example, is better to have `.box-title` instead of `.box h2`.

The *stage* category have classes that indicate state of a componente. For example: `.is-active`.

The last file, `theme` work as a `skin` of the application and is not obligatory in a SMACSS strcuture.

### BEM

BEM, *Block, Element, Modifier*, is a approach developed by a company called [Yandex](https://company.yandex.com/).

According with BEM, *block* is the higher level of a component. for example, `header` e `footer`.

The *element* is a block of code son of the *block*, it must have a functionality and to create *element* we need to use `__` as a separator. For example, if the `.menu` class is the *block*, the *element* will be `.menu__item`.

A *state* add `__` to the selector. Note that, unlike SMACSS, in BEM we need to link it to the parent selector. Example:
Block:   `.menu`;
Element: `.menu_item`;
State:   `.menu__Item__active`;

## Never underestimate CSS

Write good stylesheets isn't a easy task. Try to learn a lot about CSS architecture and code standards before learn any framework and if you're gonna use a pre-compiler, always keep an eye in the output code to make sure that it have a good performance.

Last tip: Spend time thinking and planning your code. It will save you a lot of time in the future.