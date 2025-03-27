# analyzing-mp-widget-styles
Analyzing MP Widget CSS Styles

## Current MP Default Stylesheet as of March 27, 2025

[Current Default CSS](https://github.com/bzerangue/analyzing-mp-widget-styles/blob/main/current/as-of-20250327/mppw-widgetstyles.css)

## Updated MP Default Stylesheet with a Fix, Comments, and a Couple of Re-organizing moves

1. On the Current Default Stylesheet as of March 27, 2025, there is a [global rule towards the end of the CSS stylesheet}(https://github.com/bzerangue/analyzing-mp-widget-styles/blob/3baed3bb0ca3880000eb9cdc2fe8396a0009a3f1/current/as-of-20250327/mppw-widgetstyles.css#L5344-L5347), that could redefine previous rules. Moved it to the top of the stylesheet under the Global CSS Variables, since it is a global style and applies to everything.  
  
```css
* {
    box-sizing: border-box;
    font-family: 'Helvetica Neue', Helvetica, Arial, sans-serif;
}
```  
   
2. The font-family in this global rule is hard-coded in there. Added a CSS Custom Property (CSS Variable) at the top called `--root-font-family: 'Helvetica Neue', Helvetica, Arial, sans-serif;` and defined it there. Then called the CSS Variable where it was defined in the CSS...  
  
```css
* {
    box-sizing: border-box;
    font-family: var(--root-font-family);
}
```  
  
3. Updated the Global Style... of `* { }` since it is applying the box-sizing fix, to also apply to the `::before` and `::after` pseudo-elements. 

```css
*::before,
*::after {
    box-sizing: border-box;
    font-family: var(--root-font-family);
}
```  
  
4. Moved another declaration since it was [misplaced](https://github.com/bzerangue/analyzing-mp-widget-styles/blob/3baed3bb0ca3880000eb9cdc2fe8396a0009a3f1/current/as-of-20250327/mppw-widgetstyles.css#L5445-L5448).
   - `.mppw-alert`, `.mppw-warning` was declared further down the stylesheet amongst the `.mpp-subscriptions` section. Moved up to the `.mppw-alert` declarations as the last one of the group.
5. Added Section Comments to the Subscriptions and Style Guide declarations. Also moved Style Guide Declarations to the Bottom of the Stylesheet.