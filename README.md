# Algorithm Create Layout (split by style(Layout) components)
  - Create var.css (Use pseudo class :root for write d own vars)
    - add color vars
    - add gaps vars 
      ```
        (good design system haven't to much values.We will only few gaps)
        GAPS must be fixed and only few types (3-4)
      ```
    - add width vars
      ```
        add width for titles in a sections
      ```
  - add typography.css
    - add font family for heading classes
      ```
      Example:
      .heading-sm,
      .heading-md,
      .heading-lg
      -----------
      .body-lg
      .body-lg
      -----------
      .caption (if we need)
      .address (if we need)
      -----------
      Centering class 
      [we don't use siple tag selector because 
      elements will be have center by default,
      in this text center will be value in 
      is brackets with class align-center
      ]

      :is(p, h1, h2, h3, h4, h5, h6).align-center {
        text-align: center;
      } 
      ```
  - add Layout.css
    - add :root vars for this css file
    ```
      --min-width: 320px;
      --max-width: 1440px;
      --header-height: 72px;
    ```
    - reset margin, padding, box-sizing: border-box
    - add Grid Container
      ```
      instead padding and media query
       use grid-container : 
       "Main idea :
       |flap 'minmax(16px, 1fr)' | CONTENT minmax(var(--min-width), var(--max-width)) | flap minmax(16px, 1fr)"
      .grid-container {
        --flap: minmax(16px, 1fr);
        --content: minmax(var(--min-width), var(--max-width));

        display: grid;
        grid-template-columns:
          var(--flap)
          var(--content)
          var(--flap);
      }
      ```
    - add .grid-content class to place box in content section in a grid template
      ```
      .grid-content {
        grid-column: 2 / 3;
      }
      ```
    - add .grid-content-full for full background section
      ```
        grid-column: 1 / -1
      ```
    - and also add service class
      ```
      .placement-center {
        align-self: center;
        align-items: center;
      }
      ```
  - create base button styles
    - set vars
      ```
      --btn-idle-fill: var(--clr-brown-dark); 
      --btn-active-fill: var(--clr-brown);
      --btn-label-color: white;
      --clr: var(--btn-idle-fill);
      ```
    - Reset :
      - font styles
      - line height
      - background
      - border
    - Styles base button
    - Style another button, change color and borders
      ```
      .btn.outlined {
        border-color: var(--clr);
        color: var(--clr);
      }
      ``` 
    - Styled: hover & active
    - Add deference size button
  - Create list styles (for all types list in Layout)
    - Create base-reset style for list
      ```
      .grid-list {
        --icon-size: 0;
        --row-gap: 0;
        --col-gap: 0;
        list-style: none;
        padding: 0;
      }
      ```
    - Create Grid list item
      ```
      .grid-list-item {
        display: grid;
        row-gap: var(--row-gap);
        column-gap: var(--col-gap);
      }
      ```
    - Create Grid item with icon
      ```
      .grid-list-item .icon {
        width: var(--icon-size);
        aspect-ratio: 1;
        grid-row: 1/-5;
      }
      ```
    - useful css trikes for different lists
      ```
      Here we told grid system if we have .icon add this style
      and make 2 columns also add icon min width that he has

      .grid-list-item:has(.icon) {
        grid-template-columns: min-content 1fr;
      }

      Her if we have icon and p.We place p in second column
      if we didn't have icon p will be automatically in first column

      .grid-list-item:has(.icon) p {
        grid-column: 2;
      }

      If we have only one <p> element we add to him align-self: center;
      .grid-list-item:has(.icon) p:first-of-type:last-of-type {
         align-self: center;
      }
      ```
  - Section Style
    - for section wrapper we will use flex system
      ```
      .section-content {
          display: flex;
          flex-direction: column;
          gap: var(--gap-xl);
          padding: var(--gap-xl) 0;
      }
      ```
  - After that we will use decorative styles (in style.css)
    - setup main color and background colors:
      ```
        body {
          background-color: var(--clr-grey-soft);
          color: var(--clr-grey-dark);
        }
      ```
    - add padding left to ul, it's for dots in list look better
    - reset default a style
      ```
        a {
          text-decoration: none;
          color: inherit;
        }
      ```
    - add cover & illustration this styles for responsive background and responsive img
      ```
      .cover {
        height: 720px;
        background-position-y: bottom; <- this options for your layout
        background-size: cover;
      }

      .illustration {       <- for img because img render in native resolution (img will be like background)
        width: 100%;
        height: 720px;
        object-fit: cover;
        object-position: bottom; <- this options for your layout
      } 
      ```
  - Useful properties
    ```
      - aspect-ratio - is a CSS property that allows you to control the aspect ratio (for video photos)
      
      - columns: 2 - separate your content to 2 columns (useful for <p> with text) work independently display flex & grid

      - Custom Propert - how to use:
      ----------
      ----------
      .grid-list {
        --col-gap: 0;
      }
      ----------
      ----------
      .grid-list-item {
        column-gap: var(--col-gap);
      }
      ----------
      ----------
      .premises-list {
        --col-gap: var(--gap-sm);
      }

    - Use :is and :has
    - white-space
    ```