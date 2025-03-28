- ### Methods of Adding JavaScript

  #### A. Inline JavaScript

  - How to Implement:

    - Add JavaScript directly in an HTML attribute. For example, use the `onload` attribute on the `<body>` tag.

    - Example:

      ```html
      <body onload="alert('Hello');">
      ```

  - Quotation Issue:

    - When a string inside the JavaScript code uses the same quotation marks as the attribute, the browser might misinterpret the code.
    - **Solution:** Use single quotes inside the double quotes (or vice versa) to avoid conflicts.

  - Downsides:

    - Difficult to maintain and debug.
    - Not modular.
    - Generally considered bad practice.

  ------

  #### B. Internal JavaScript

  - How to Implement:

    - Place JavaScript code between `<script>` tags within the HTML file.

    - Example:

      ```html
      <script type="text/javascript">
        alert("Hello");
      </script>
      ```

  - Benefits:

    - Easier to write than inline JavaScript.
    - Avoids the nested quotation problem.

  ------

  #### C. External JavaScript

  - How to Implement:

    - Write JavaScript code in a separate file (e.g., `index.js`).

    - Link the file in the HTML using a `<script>` tag with the `src` attribute.

    - Example:

      ```html
      <script src="index.js"></script>
      ```

  - Benefits:

    - Keeps HTML clean and maintains a clear separation of structure, style, and behavior.
    - Enhances modularity and reusability.

  ------

  ### 4. Importance of Script Placement in HTML

  - **CSS vs. JavaScript Placement:**

    - **CSS:** Typically placed in the `<head>` so that styles are applied before content is rendered.
    - JavaScript:
      - Placing the `<script>` tag at the top (inside `<head>`) can lead to errors if the script tries to manipulate elements that haven’t been rendered yet.
      - Example Error: "Cannot set property 'innerHTML' of null" occurs when the script runs before the `<h1>` element exists.

  - **Best Practice:**

    - Place the `<script>` tag at the end of the HTML document, just before the closing `</body>` tag.
    - Reason:
      - Ensures that all HTML elements are fully loaded before any JavaScript code runs.
      - Improves the perceived loading time of the website since content is rendered first.

  