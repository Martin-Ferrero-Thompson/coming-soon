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
"*"  (Universal Selector):
This selector targets all HTML elements.
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