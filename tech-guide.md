# style.css Breakdown

This document provides a detailed explanation of the `style.css` file, including its overall functionality and a breakdown of each CSS selector and how it styles the HTML elements in `index.html`.

## Table of Contents

1.  [Functionality Overview](#functionality-overview)
2.  [Detailed Selector Explanations](#detailed-selector-explanations)
    * [1. User-Agent Reset](#1-user-agent-reset)
    * [2. Root Variables](#2-root-variables)
    * [3. Base Styles](#3-base-styles)
    * [4. Main Content Styles](#4-main-content-styles)
    * [5. Heading and Paragraph Styles](#5-heading-and-paragraph-styles)
    * [6. Layout Styles](#6-layout-styles)
    * [7. Header Styles](#7-header-styles)
    * [8. Footer Styles](#8-footer-styles)
    * [9. Media Queries](#9-media-queries)

## Functionality Overview

The `style.css` file is responsible for styling the `index.html` landing page. It includes:

* **Reset Styles:** A user-agent reset to normalize default browser styles.
* **Root Variables:** CSS variables for consistent colors, fonts, and spacing.
* **Base Styles:** Styles for basic HTML elements like `body`, `h1`, `p`, etc.
* **Layout Styles:** Styles for the overall page layout, including the content container and wrapper.
* **Component Styles:** Styles for specific components like the header, footer, brand name, and social links.
* **Media Queries:** Responsive styles for different screen sizes.

The file is organized to be maintainable and readable, with styles grouped logically and using CSS variables for easy adjustments.

## Detailed Selector Explanations

### 1. User-Agent Reset

```css
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
```
* "*"  (Universal Selector):
  * This selector targets all HTML elements.
  * **margin: 0;** removes default margins from all elements.
  * **padding: 0;** removes default padding from all elements.
  * **box-sizing: border-box;** changes the box model to include padding and borders in the element's total width and height, making layout calculations more predictable.

### 2. Root Variables

```css
:root {
  --brand-accent-color: #8214e0;
  --brand-name-black: #222222;
  --body-text-color: #222222;
  --body-background-color: #f0f0f0;
  --heading-font-family: 'Montserrat', sans-serif;
  --body-font-family: 'Roboto Condensed', sans-serif;
  --presents-font-family: 'Cormorant Garamond', serif;
  --main-element-spacing: 1rem;
}
```
* :root:
  * This pseudo-class targets the root element of the document (usually <html>).
  * It defines CSS variables that can be used throughout the stylesheet.
  * These variables store color values, font families, and spacing values, allowing for easy updates and consistency.

### 3.  Base Styles

```css
html {
  font-size: 16px;
  height: 100%;
}

body {
  font-family: var(--body-font-family);
  text-align: center;
  margin: 0;
  background: linear-gradient(to bottom, #D0A3F0, #8214e0);
  background-size: cover;
  background-repeat: no-repeat;
  height: 100vh;
  color: var(--body-text-color);
}

body::before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.1);
}

main,
header,
footer {
  position: relative;
}
```
* html:
  * Sets the base font size and the height of the <html> element.
* body:
  * Applies the body font family, text alignment, background gradient, and text color.
  * **height: 100vh;** makes the body take up the full height of the viewport.
* body::before:
  * Creates a pseudo element that covers the entire body.
  * It adds a semi-transparent overlay to the background gradient.
* main, header, footer:
  * Sets the position of the main, header, and footer elements to relative, which is used to establish a positioning context for their children.

### 4. Main Content Styles

```css
main h1,
main h2,
main p {
  margin-top: var(--main-element-spacing);
  margin-bottom: var(--main-element-spacing);
}

main h1:first-child,
main h2:first-child,
main p:first-child {
  margin-top: 0;
}

main p {
  padding-bottom: var(--main-element-spacing);
  max-width: 74ch;
  margin: var(--main-element-spacing) auto;
  line-height: 1.7;
  text-align: start;
  font-size: 1.5rem;
  letter-spacing: 0.05rem;
}
```
* main h1, main h2, main p:
  * Targets `<h1>`, `<h2>`, and `<p>` elements that are direct descendants of the `<main>` element.
    * Applies a top and bottom margin to these elements, using the `--main-element-spacing` CSS variable for consistency. This ensures uniform vertical spacing between the headings and the paragraph w  ithin the main content area.
* main h1:first-child, main h2:first-child, main p:first-child:
  * Targets the first `<h1>`, `<h2>`, and `<p>` elements within the `<main>` element.
    * Sets the top margin of these first elements to 0. This is to remove the top margin that would otherwise be applied by the previous rule, preventing extra space at the top of the main content area.
* main p:
  * Targets the paragraph `<p>` element within the `<main>` element.
    * **padding-bottom: var(--main-element-spacing);** adds padding to the bottom of the paragraph, using the same spacing variable to match the margins.
    * **max-width: 74ch;** sets a maximum width for the paragraph, ensuring it doesn't stretch too wide on larger screens, which improves readability.
    * **margin: var(--main-element-spacing) auto;** centers the paragraph horizontally and adds the specified margin.
    * **line-height: 1.7;** sets the line height, improving text readability by adding vertical space between lines.
    * **text-align: start;** aligns the text to the start (left for left-to-right languages).
    * **font-size: 1.5rem;** sets the font size of the paragraph.
    * **letter-spacing: 0.05rem;** adds a small amount of letter spacing, improving the overall visual appearance of the text.
