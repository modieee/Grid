# Introduction to Grid

Grid is a layout technique property in CSS used to dynamically arrange content on a web page.

## Overview

- How to create grid layouts
- How to position grid items
- Differences between flexbox and grid
- Describe a situation for using grid over flexbox

### A look back and Flexbox

Flexbox is a very useful tool for building 1 dimensional layouts and its `flex-wrap` property is even more impressive as it allows for developer to stack content and build 2 dimensional layouts on a webpage.

Flexbox is really impressive but when it comes to more complicated stuff although it can do the work well, it often involves a lot of tinkering.

### What is a Grid?

Grid is also a layout technique which was released in 2017. The idea for a grid layout of the webpage came from the grid-like structure of magazines and newspapers.

## Creating a Grid

### Overview

- Making a Grid container
- Defining grid track
- Explain the difference between implicit and explicit grid
- Set gaps between grid cells.

## Setting up a Grid

To set up a CSS grid on any element you must think about the element in terms of container and items.

### Grid Container

Grid containers jsut as the name implies "contains" the whole grid, and in CSS an element can be marked as a contianer by changing the `display` property and in this case we are setting the display property to `grid` i.e, `display: grid;`.

When this applied to any element the element becomes a grid container and the elements nested directly within the grid container automatically become grid items.

```CSS
<!-- index.html -->

<div class="container">
  <div>Item 1</div>
  <div>Item 2
    <p>I am not a grid item!</p>
  </div>
  <div>Item 3</div>
  <div>Item 4</div>
</div>
```

Grid items can also become grid containers, all you have to do is apply the grid display property to it.

#### Lines and tracks in grids

Use inspect elements on your webpage in developer tools to see the grid badges on the grid elements in the code. The layout options allows you to set an overlay  that can show the invisible lines, tracks and areas of the grid. Grid tracks are defined by using `grid-template`, and can be thought of as any single row or column

#### Columns and rows

Columns and rows define a a grids' grid track (the space between lines on a grid).
The properties `grid-template-columns` and `grid-template-rows` make defining column and row tracks easy.

```CSS
.container {
  display: grid;
  grid-template-columns: 50px 50px;
  grid-template-rows: 50px 50px;
}
```
CSS Grid also includes a shorthand property for defining rows and colums. `grid-template-columns` and `grid-template-rows` can be replaced with `grid-template`,with this shorthand rows and columns are defined together with a slash for seperation. After the slash is for the row and before the slash is for the column.

```CSS
/* styles.css */

.container {
  display: grid;
  grid-template: 50px 50px / 50px 50px 50px;
}
```

## Explicit and Implicit Grid

When you use the `grid-template-columns` and `grid-template-rows` properties you are explicitly defining grid tracks to layout to layout your grid items. But when the grid needs more tracks for extra content, it will implicitly define new grid tracks. Also the size value set in `grid-template-columns` and `grid-template-rows` properties are not carried over into these implicit grid track, but we can define values for the implicit gird tracks.

Implicit grid track size can be set using `grid-auto-rows` and `grid-auto-columns` properties. like this new can be the same values as the explicit row track sizes, e.g.

```CSS
/* styles.css */

.container {
  display: grid;
  grid-template-columns: 50px 50px;
  grid-template-rows: 50px 50px;
  grid-auto-rows: 50px;
}
```

By default, CSS Grid will add additional content with implicit rows. This means the extra elements would keep being added further down the grid in a vertical fashion. Extra content can be added horizontally using `grid-auto-flow: column` property and those implicit track sizes can be defined with `grid-auto-columns` property.

## Gap

The gap between grid rows and columns is known as the gutter or alley. Gap sizes can be adjusted separately for rows and columns using the `column-gap` and `row-gap` properties.

## Positioning Grid Elements

### Overview

- Define the difference between tracks, lines and cells.
- Position Items by defining their start and end lines.
- Use Shorthand notation

## Reviewing Tracks

Grid tracks can be thought of as any single row or column on a grid

## Lines

Grind lines are created implicitly after the grid tracks have been defined and cannot be explicitly created.
Every track has a start line and end line and the numbers are numbered from left to right and top to bottom starting at 1.

## Cells

Think of cells like a cell in a spreadsheet, it's a space defined by a row, column coordinate. By default each child element of a grid container will occupy one cell.

## Positioning

[Read this section of the study](https://www.theodinproject.com/lessons/node-path-intermediate-html-and-css-positioning-grid-elements#positioning)

## Advanced Grid Properties

### Overview

- `repeat()` function in grid
- Fractional units `fr`
- min/max and ideal track size boundaries
- Use `auto-fit` and `auto-fill` to create grid with dynamic number of rows and columns
- Use `auto-fit`/`auto-fill` alongside `minmax()` to create responsive grid.

```CSS
resize: both;
overflow: none;
```

The above CSS Properties when used together on any container, makes the container resizeable in the broswer.

## Fraction units

[Read this](https://chatgpt.com/share/68edcb30-b0f8-8007-b1ce-995a6d2c518f), [this](https://medium.com/flexbox-and-grids/the-css-fractional-unit-fr-in-approachable-plain-language-fdc47bd387f7) and [this](https://www.theodinproject.com/lessons/node-path-intermediate-html-and-css-advanced-grid-properties#fractional-units).

## Dynamic minimum and maximum sizes

`minmax()` - is a CSS function that is specifically used with Grid. It can only be used with the following CSS properties:

- `grid-template-columns`
- `grid-template-rows`
- `grid-auto-columns`
- `grid-auto-rows`

`minmax()` quite literarily means:

1. minimum size the grid track can be
2. maximum size the grid track can be

```CSS
.grid-container {
  grid-template-rows: repeat(2, 1fr);
  grid-template-columns: repeat(5, minmax(150px, 200px));
}
```

## auto-fill and auto-fit

`auto-fill` and `auto-fit` are values that belong to the `repeat()` function of CSS Grid. They always return "The largest possible integer" without the grid items overflowing their container.

```CSS
.example {
  display: grid;
  width: 1000px;
  grid-template-columns: repeat(auto-fit, 200px);
}
```
