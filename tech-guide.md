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

### 5.  Heading and Paragraph Styles
```css
h1 {
  font-family: var(--heading-font-family);
  font-weight: 500;
  color: transparent;
  font-size: 4rem;
  letter-spacing: 2rem;
  text-transform: uppercase;
  background-image: linear-gradient(to right, #8214e0, #6A5ACD, #483D8B);
  -webkit-background-clip: text;
  background-clip: text;
}

h2 {
  font-family: var(--heading-font-family);
  font-weight: 500;
  font-size: 2.5rem;
  letter-spacing: 0.3rem;
}
```

* h1:
  * Targets all `<h1>` elements on the page.
    * **font-family: var(--heading-font-family);** sets the font family using the --heading-font-family CSS variable.
    * **font-weight: 500;** sets the font weight.
    * **color: transparent;** makes the text transparent, allowing the background gradient to show through.
    * **font-size: 4rem;** sets the font size.
    * **letter-spacing: 2rem;** adds a large amount of letter spacing, creating a dramatic effect.
    * **text-transform: uppercase;** transforms the text to uppercase.
    * **background-image: linear-gradient(to right, #8214e0, #6A5ACD, #483D8B);** applies a linear gradient background to the text.
    * **-webkit-background-clip: text; and background-clip: text;** clip the background gradient to the text, making it appear as if the text itself has the gradient.
* h2:
  * Targets all `<h2>` elements on the page.
    * **font-family: var(--heading-font-family);** sets the font family using the --heading-font-family CSS variable.
    * **font-weight: 500;** sets the font weight.
    * **font-size: 2.5rem;** sets the font size.
    * **letter-spacing: 0.3rem;** adds letter spacing, enhancing the visual appearance of the heading.
* p:
    * Targets all `<p>` elements on the page.
    * **max-width: 74ch;** sets a maximum width for the paragraph, ensuring it doesn't stretch too wide on larger screens, which improves readability.
    * **line-height: 1.7;** sets the line height, improving text readability by adding vertical space between lines.
    * **text-align: start;** aligns the text to the start (left for left-to-right languages).
    * **font-size: 1.5rem;** sets the font size of the paragraph.
    * **letter-spacing: 0.05rem;** adds a small amount of letter spacing, improving the overall visual appearance of the text.

### 6. Layout Styles

```css
.content-container {
  max-width: 1440px;
  margin: 0 auto;
  padding: 20px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
}

.content-wrapper {
  border: 2px solid F8F8F8;
  padding: 40px 20px;
  border-radius: 10px;
  box-sizing: border-box;
  width: 90%;
  background-color: rgba(248, 248, 248, 0.9);
  display: flex;
  flex-direction: column;
}
```
* .content-container:
  * Sets the maximum width, centers the container, adds padding, and uses flexbox to center its content vertically and horizontally.
    * **min-height: 100vh;** makes the container take up the full height of the viewport.
    * **.content-wrapper:** 
        * Adds a border, padding, border radius, box sizing, width, and background color.
        * Uses flexbox to arrange its content in a column.

### 7. Header Styles
```css
header {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.brand-name {
  font-family: var(--heading-font-family);
  font-size: 2.2rem;
  font-weight: bold;
  line-height: 1.2;
  letter-spacing: 0.3rem;
  text-align: start;
  display: inline-block;
  text-transform: uppercase;
  margin-bottom: 5px;
}

.accent-first {
  color: var(--brand-accent-color);
}

.brand-name span:last-child {
  color: var(--brand-name-black);
  display: block;
}

.brand-name-short {
  font-family: var(--heading-font-family);
  font-weight: bold;
  font-size: 1.5rem;
  letter-spacing: 0.3rem;
}

.brand-name-short span:last-child {
  color: var(--brand-accent-color);
}

.presents-announcement {
  font-family: var(--presents-font-family);
  font-weight: 700;
  font-size: 2.75rem;
  letter-spacing: 0.3rem;
  text-align: center;
  margin-top: 5px;
  margin-bottom: 45px;
}
```
* **header:**
  * Uses flexbox to arrange the header content in a column and centers it horizontally.
* **.brand-name:**
  * Styles the brand name with font family, font size, font weight, line height, letter spacing, text alignment, display, text transformation, and margin.
* **.accent-first:**
  * Applies the accent color to the first word of the brand name.
* **.brand-name span:last-child:**
    * Styles the last `<span>` element within the brand name with the brand name black color and sets its display to block.
* **.brand-name-short:**
    * Styles the short brand name with font family, font weight, font size, and letter spacing.
* **.brand-name-short span:last-child:**
    * Applies the accent color to the last `<span>` element within the short brand name.
* **.presents-announcement:**
    * Styles the "Presents" announcement with font family, font weight, font size, letter spacing, text alignment, and margins.

### 8. Footer Styles

```css
footer {
  width: 100%;
  text-align: center;
}

.footer-content {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-top: 50px;
  margin-left: 50px;
  margin-right: 50px;
  font-size: 1.5rem;
}

.footer-left,
.footer-center,
.footer-right {
  flex: 1;
  display: flex;
  align-items: center;
  justify-content: center;
}

.footer-left {
  text-align: left;
  justify-content: flex-start;
  display: inline-flex;
  align-items: center;
}

.footer-right {
  text-align: right;
  justify-content: flex-end;
}

.footer-left a {
  color: var(--body-text-color);
  text-decoration: none;
  margin-left: 0;
}

.footer-left a:hover {
  color: var(--brand-accent-color);
}

.footer-left .material-symbols-outlined {
  margin-right: 5px;
  font-size: 1.5rem;
  color: var(--brand-accent-color);
}

.social-links a {
  display: inline-block;
  margin: 0 10px;
}

.social-links img {
  width: 1.5rem;
  height: 1.5rem;
  transition: opacity 0.3s ease;
  filter: invert(36%) sepia(61%) saturate(2259%) hue-rotate(237deg) brightness(91%) contrast(90%);
}

.social-links img:hover {
  opacity: 0.7;
  filter: invert(46%) sepia(71%) saturate(2359%) hue-rotate(247deg) brightness(101%) contrast(100%);
}
```
* **footer:**
  * Sets the width and text alignment of the footer.
* **.footer-content:**
    * Uses flexbox to create a layout with space between elements, centers items vertically, and adds margins and font size.
* **.footer-left, .footer-center, .footer-right:**
    * Uses flexbox to distribute space equally and centers items.
* **.footer-left:**
    * Aligns text to the left, aligns items to the start, and uses inline flexbox to align items.
* **.footer-right:**
    * Aligns text to the right and aligns items to the end.
* **.footer-left a:**
    * Styles the email link with text color, removes text decoration, and removes left margin.
* **.footer-left a:hover:**
    * Changes the email link color on hover.
*  **.footer-left .material-symbols-outlined:**
    * Adds spacing, font size, and color to the email icon.
* **.social-links a:**
    * Makes the social links inline blocks and adds margins.
* **.social-links img:**
    * Sets the width, height, transition, and color filter for the social media icons.
* **.social-links img:hover:**
    * Changes the opacity and color filter of the social media icons on hover.

### 9. Media Queries
```css
@media (min-width: 1440px) { /* xxl breakpoint */
  .content-container {
    max-width: 1440px;
  }
}

@media (min-width: 1200px) { /* xl breakpoint */
  .content-container {
    max-width: 1200px;
  }
}

@media (min-width: 992px) { /* lg breakpoint */
  .content-container {
    max-width: 992px;
  }
  .content-wrapper {
    padding: 80px 20px;
  }
  h1 {
    font-size: 5rem;
  }
}

@media (min-width: 768px) { /* md breakpoint */
  .content-container {
    max-width: 768px;
  }
  .content-wrapper {
    padding: 60px 20px;
  }
  h1 {
    font-size: 4.5rem;
  }
}
```