Documenting the Omnifood Project steps, to look back when I start with black HTML page.
///
smooth scrolling and sticky nav left
///

> Refer to the PDF, this md, and the code to understand well.

From PDF:

1. Defining & Planning the project
2. Sketching initial layouts

# Initial Set-ups

Get together your images, and content text in a folder.

## Initial HTML set-up

Doctype stuff

## Initial CSS set-up

```css
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

html {
  /* 10px /  16px = 0.625 = 62.5% */
  /* Percentage of user's browser font-size setting */
  /* easier to use rem as 1rem = 10px (by deafult, obv) */
  font-size: 62.5%;
}

body {
  font-family: sans-serif;
  line-height: 1;
  font-weight: 400;
  color: #555;
}
```

- I can build up on which one would look good, after some of the components are built, hence initially font-family is sans-serif,
- color being pure black can be a bit overwhelming, hance any grey color would be fine.

---

### Design settings:

- It is always better to have design settings like font & spacing systems, main & body color fo the webpage and many more being handy at the top of CSS page.

```css
/*
---01 TYPOGRAPHY SYSTEM
  
- font sizes (px)
10 / 12 / 14 / 16 / 18 / 20 / 24 / 30 / 36 / 44 / 52 / 62 / 74 / 86 / 98

- font weights
default: 400

- line height
default: 1



--- 02 COLORS

- Primary: #e67e22
- Tints: 
- Shades: 
- Accents:
- Greys: #555


--- 05 SHADOWS


--- 06 BORDER RADIUS


--- 07 WHITESPACE

- Spacing System (px)
2 / 4 / 8 / 12 / 16 / 24 / 32 / 48 / 64 / 80 / 96 / 128

*/
```

### Tips

- Always begin with responsiveness in mind (PDF)
- Use of rem, max-width, %, viewposrt relativeness etc.
- Try segregating css designs based on diff components being styled & general reusable blocks.
- Try creating standalone components in your page like links, buttons, list & their items. (It's al subjective ATEoD)
- Basics for reusable UI components.

- finish inner then layout, well its just subjective atp.
- always try checking the contrast ratios with coolors contrast checker
- using aside tag for pricing inc taxes, stuff not that imp

# Hero section

- Proceed with semantic HTML
- section is used to differentiate between normal container and huge sections.
- Many sections can be inside a body.
- Always prefer using class selectors instead of ID or element, this will create consistency.
- Anchor elements (links) are used for going somewhere in that page or other page, and buttons should be used for some actions only.
- Always better to use same layout style for main sections, like Grid.

> Hence used grid for Hero even though it looks like 1D, and Grid just creates equally spaced columns easily.

- Never skip alt for images as it is useful for SEO and for users where images werent loaded. Being desriptive is fine.
- Always go from layout perfect (with responsivity), then individual styles.
- In styling, first tackle typography then spacing etc, basically go order wise to maintain consistency.

## Trick01:

- Adding borders when a button is hovered will lead to layout jump, hence add box-shadow (using inset) to add "border" inside the element.

```css
.btn--outline:hover,
.btn--outline:active {
  background-color: #fdf2e9;
  /* border: 3px solid #fff;  this would add border to the outside of the element which would lead to the layout jumping each time hovered.*/

  /* inset keyword adds shadow inside */
  box-shadow: inset 0 0 0 3px #fff;
}
```

## TRick02

- Using transition property, to avoid blank changes.
- used on the original state (here the link/visited state)

```css
transition: <property to transition> | duration | type;

transition: background-color 0.5s;
```

## Trick03

- using helper classes are good for standalone components.
- say you want to use element styles (.btn class) later on in page, but adding a specific property just for one use-case will disrupt its next use, hence use helper classes on the required element.

## Trick04

- overlapping images by making margin-right negative and adding border to seperate.

## Trick05

- Making one letter of different color(property)
- Done by wrapping it in span element and styling it

## Trick06

- 1fr 1fr alone: Columns may not be equal if one column has content that can’t shrink.
- minmax(0, 1fr): Tells the browser: “Don’t let content force the column to stay big — let it shrink to 0 if needed.”

<details>
  <summary>More details</summary>
1fr 1fr splits leftover space, but doesn’t force equal widths if one column can’t shrink.

By default, columns won’t shrink smaller than their content.

So if one side has long text, it resists shrinking; the image gets squeezed.

minmax(0, 1fr) allows both columns to shrink to zero if needed.

Result: True equal columns, even with inflexible content.

</details>

## Trick07

- Always try to create reusable classes, like container (with width, centering, padding etc), grid sections.

```css
.container {
  max-width: 120rem;
  margin: 0 auto;
  padding: 0 3.2rem;
}

.grid--center-v {
  align-items: center;
}

.grid {
  display: grid;
  gap: 9.6rem 6.4rem;
}

.grid--2-cols {
  grid-template-columns: repeat(2, minmax(0, 1fr));
}
```

- If adding any visual styles, try doing it in css, the circles in How-It-Works section are done in css.

## Trick08

- Not really a trick, btw.
- Useage of svg for icons(ex: heroicons) just clusters up the html doc if we are using a lot of icons.
- Hence use a script that can give a unique html element to work on

---

### Dump

- its always better to make links (li elements or anything) to be inline-block.
  for padding purpose
- using end selector to ensure it always applies (increases specificity)

- creating reusable classes, which can be used in any element to get desiarable ouptus.

example: a container class, to be added on a container div, which can have:

.container{
max-width: 120rem;
margin: 0 auto;
padding: 0 3.2rem;
}
side-note: max-width is widely used as 1200px or 1140px,

we used 1200px with a padding of 32px, hence main content is 1136px, similar to 1140px

similarly a reuasble grid class can also be created with base properties in it. and specific classes with grid--2-cols, grid--3-cols etc can be made

this coulve been added to the container of hero section, but usually, hear section should be a bit wider than rest i,e., 130rem.

- using pseudo element to create those circles. pseudo elements insert a child element. pseudo elements cannot be added to img as creating childs for imgs is not allowed in HTML

- when you want an empty content block, set width as some % and padding bottom to aome %, coz width and height togoether wont work on empty content

- using filter property to greyout and reduce brightness of featured in images

- not needed to put fixed sizes on images for meals sections,

since grid divides spaces equally, having width as 100% for meals images would just be fine and actually good

- another way to arrange list items without hussle, is by using the FLEX.

change direction to column and done.

alignitems - horizontal

gap - margin-bottom

- for box-shoadow, ideally only vertical shadow, with spread-radius dowble of it, then rgba for color

- using overflow to avoid image being overflowen after we kept the border radius.
  overflow: hidden;

- using currentColor for same class styling, which creates consistency

- for links (created by <a> tag)

```css
link:link,
.link:visited {
  //some properties
}

.link:hover,
.link:active {
  //some properties
}
```

- for transitioning, if we remove the border during hover, it messes with the layout, hence use transperant border

- can use hover on elements which are not links !

- using transform: translateY(-1rem); translateY only goes in Y direction.

- using figure elements as container for block of images or just images and also for testimonials and blockquote for their quotes

- we can use figcaption element inside figure elements, which is req for images.

- chaging cols from 1fr 1fr to 55fr 45fr equivalent to 1fr 0.8fr
  keep in mind, align items are default stretch

- we can use transform property with various values like rotate, scale, translate etc

```css
.class {
  transform: rotate(45deg);
  transform: translateX(-50, -50);
  transform: scale(1.1);
}

//make sure use transition & overflow if required
```

- for the best value tag, we used transform rotate property & played around the values to find the right position

- in the testimonials section, there are two grids as siblings (basically two child grid inside section-testimonials), hence we require a margin-bottom for them.
  but by putting it to grid class, it will break prev arrangements.
  hence remove margin-botton=m when for the grid which is the last child

- or just use

```css
.grid:not(:last-child) {
  //something
}
```
