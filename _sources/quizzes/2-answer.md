# Quize 2

Given the following DOM tree, please write the CSS selectors using the shortest possible expressions to target the specified text nodes. You may appropriately use pseudo-classes such as `:first-child`, `:last-child`, `:nth-child`, `:first-of-type`, etc.

```html
<body>
  <h1>One</h1>
  <p class="gv">
    <b>Two</b><span><b>Three</b><b>Four</b></span>
  </p>
  <div>
    <ol id="fv">
      <li>Five</li>
      <li>Six</li>
    </ol>
  </div>
  <h1 id="me">Seven</h1>
  <p><b>Eight</b></p>
  <ol>
    <li>Nine</li>
    <li>Ten</li>
  </ol>
</body>
```

You can verify your answer by using the following CSS code:

```css
your-css-selector {
  color: red;
}
```

**Example Question**

- **Only** Node "one":

- Answer: `h1:first-child` or `h1:first-of-type`

---

1. **Only** Node "Two": `p.gv > b`

2. **Only** Node "Three": `p.gv > span > b:first-child`

3. **Only** Node "Eight": `p:nth-of-type(2) > b`
4. **Only** Node "Ten": `body > ol:last-child > li:nth-child(2)`
5. **Only** Node "Twelve": `ul > li:last-child`

6. You UI design team has decided on the following layout for the front page of your web app:

   - The height of the top navigation is 40px
   - The height of the app status and notification messages is 60px
   - The left and right panel take 25% of the width each
   - The app status and notification message panel takes 50% of the width each

   ```{image} ../assets/img/layout.jpg
   :alt: dom
   :width: 800px
   :align: center
   ```

   Given the HTML below, use CSS and the CSS Grid layout to recreate the design depicted in the image above.

   ```html
   <body>
     <div id="container">
       <div class="top-nav"></div>
       <div class="left-panel"></div>
       <div class="right-panel"></div>
       <div class="main-panel"></div>
       <div class="app-status"></div>
       <div class="notification"></div>
     </div>
   </body>
   ```

   ```css
   <style>
    body,
    html {
      /* height:100%; */

      margin: 0px;
    }
    #container {
      display: grid;
      gap: 5px;
      height: 100vh; /* Use viewport height to cover the entire screen height */
      width: 100vw; /* Use viewport width to cover the entire screen width */

      /* Set row sizes: top row is 40px, bottom row is 60px, and the middle row takes up the rest of the space */
      grid-template-rows: 40px 1fr 60px;

      /* Defined four equal-width columns */
      grid-template-columns: 1fr 1fr 1fr 1fr;
      grid-template-areas:
        "nav nav nav nav"
        "left main main right"
        "app app notification notification";
    }

    .top-nav {
      background-color: blue;
      grid-area: nav;
    }
    .left-panel {
      background-color: red;
      grid-area: left;
    }
    .main-panel {
      background-color: green;
      grid-area: main;
    }
    .right-panel {
      background-color: orange;
      grid-area: right;
    }
    .notification {
      background-color: yellow;
      grid-area: notification;
    }
    .app-status {
      background-color: purple;
      grid-area: app;
    }
   </style>
   ```
