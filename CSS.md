# CSS
## Introduction
- **CSS** is a Web standard and it stands for **Cascading Style Sheets**.
```css
p {
  color: red;
}
```
- This CSS rule sets all paragraphs to be displayed in red instead of black, the default color.
- A CSS rule set has one part called the **selector**, and the other part called the **declaration block**.
- The declaration contains various declarations, each composed of a property, and a value.
-  `p` is the selector. It applies the following rules to all elements using the `p` tag on the page. And `color: red;` is the only declaration contained in the declaration block.
- You can put this CSS in a `style` tag in the head of an HTML document: 
```css
<style>
  p {
    color: red;
  }
</style>
```
-  Or, you can put it in a separate `style.css` file and then load it in the HTML head:
```css
<link href="style.css" rel="stylesheet" />
```
- This is more common when you have lots of CSS, which is what happens normally. CSS in the `head` of the HTML document works until a certain level, then it’s too painful to manage.
- Another way, useful for "quick fixes", is to use the `style` attribute on an HTML element:
```css
 <p style="color: red">test</p>
 ```
- Multiple CSS can be listed one after the other:
```css
p {
  color: red;
}

a {
  color: blue;
}
```
- A selector can target one or more items:
```css
p, a {
  color: red;
}
```
- Spacing is meaningless in CSS. This means you could write the above CSS as:
```css
p,a {
  color: red;}
```
```css
p,a {              color: red;
         }
```
- It’s important that each declaration ends with a semicolon ;.\


## Colors
- The two main properties are `color` and `background-color`.
### Named colors
- we have CSS keywords that define colors
- Like `white`
  -  `black`
  -  `red`
  -  `blue`
  -  `yellow`
  -  `darkviolet`
  -  `floralwhite`
  -  `forestgreen`
### RGB and RGBa (`rgb()` / `rgba()`)
- You can use `rgb()` to calculate a color from its RGB color code, which sets the color based on its red-green-blue parts ranging from 0 to 255:
```css
p {
  color: rgb(255, 255, 255); /* white */
  background-color: rgb(0, 0, 0); /* black */
}
```
- `rgba()` lets you add the alpha channel to enter a *transparent part*, so the image can be see-through. That can be a number from 0 to 1:
```css
p {
  background-color: rgba(0, 0, 0, 0.5);
}
```
### Hexadecimal notation (#nnnnnn)
- Another commonly used option is to express the RGB parts of the colors in hexadecimal notation, which is composed of 3 blocks.
- `black`, which is `rgb(0,0,0)` in RGB is expressed as `#000000`.
- We can shortcut the 2 numbers in each pair to 1 if they are equal, so it becomes `#000`.
-  `white`, `rgb(255,255,255)` can be expressed as `#ffffff` or `#fff`.
-  The hexadecimal notation lets express a number from 0 to 255 in just 2 digits since they can go from 0 to “15” (f).
-  Not all browsers support the shortened notation, so use all 6 digits to express the RGB part.

## More selectors
- We can select elements with a class using this syntax: `.class {}`.
```css
<p class="dog-name">Roger</p>
```
```css
.dog-name {
  color: yellow;
}
```
- To select elements with a specific id, we can use this syntax: #id {}
```css
<p id="dog-name">Roger</p>
```
```css
#dog-name {
  color: yellow;
}
```
- There is one big difference between those two selectors.
- Inside an HTML document, you can repeat the same class value across multiple elements, but you can only use an id once.
- Using classes you can select an element with 2 or more specific class names, something not possible using ids.
- You can target an element that has 2 (or more) classes together by combining the class names separated with a dot, without spaces.
```css
<p class="dog-name roger">Roger</p>
```
```css
.dog-name.roger {
  color: yellow;
}
```
- In the same way, you can combine a class and an id.
```css
<p class="dog-name" id="roger">Roger</p>
```
```css
<p class="dog-name" id="roger">Roger</p>
```
- You can create a more specific selector by combining multiple items to follow the document tree structure. For example, if you have a `span` tag nested inside a `p` tag, you can target that one without applying the style to a `span` tag not included in a `p` tag:
```css
<span> Hello! </span>
<p>
  My dog's name is:
  <span class="dog-name"> Roger </span>
</p>
```
```css
p span {
  color: yellow;
}
```
- To make the dependency strict to the first level, you can use the > symbol between the two tokens:
```css
p > span {
  color: yellow;
}
```
- if a span is not a first children of the p element, it’s not going to have the new color applied.
- Direct children will have the style applied:
```css
<p>
  <span> This is yellow </span>
  <strong>
    <span> This is not yellow </span>
  </strong>
</p>
```
- Adjacent sibling selectors let us style an element only if preceded by a specific element. We do so using the + operator:
```css
p + span {
  color: yellow;
}
```
- This will assign the color yellow to all span elements preceded by a `p` element:
```css
<p>This is a paragraph</p>
<span>This is a yellow span</span>
```
## Cascade
- CSS means Cascading Style Sheets.
- Cascade is a fundamental concept of CSS.
- Cascade is the process, or algorithm, that determines the properties applied to each element on the page. Trying to converge from a list of CSS rules that are defined in various places.
- It does so by taking into consideration:
  -  *specificity*
  - *importance*
  - *inheritance*
  - *order of the CSS rule in the file*
- Even if you just have one CSS file loaded by your page, there is another CSS that is going to be part of the process. We have the browser (user agent) CSS.
- Then your CSS comes into play.
- Then the browser applies any user stylesheet, which might also be applied by browser extensions.
- All those rules come into play while rendering the page.
```css
<p class="dog-name">Roger</p>
```
- We can have
```css
.dog-name {
  color: yellow;
}
```
- and another rule that targets `p`, which sets the color to another value:
```css
p {
  color: red;
}
```
And another rule that targets `p.dog-name`:
```css
p.dog-name {
  color: red;
}
```
- Which rule is going to take precedence over the others
- The more specific rule will win.
- If two or more rules have the same specificity, the one that appears last wins.
## Specificity
- Specificity is calculated using a convention.
- We have 4 slots, and each one of them starts at 0: `0 0 0 0`.
-  The slot at the left is the most important, and the rightmost one is the least important.
-  We increase this value when we have an **element selector**.
-  An element is a tag name. If you have more than one element selector in the rule, you increment accordingly the value stored in this slot.
```css
p {} /* 0 0 0 1 */
span {} /* 0 0 0 1 */
p span {} /* 0 0 0 2 */
p > span {} /* 0 0 0 2 */
div p > span {} /* 0 0 0 3 */
```
- The **second slot** is incremented by 3 things:
  - class selectors
  - pseudo-class selectors
  - attribute selectors
- Every time a rule meets one of those, we increment the value of the second column from the right.
```css
.name {} /* 0 0 1 0 */
.users .name {} /* 0 0 2 0 */
[href$='.pdf'] {} /* 0 0 1 0 */
:hover {} /* 0 0 1 0 */
```
- Here’s what happens when you combine “slot 2” selectors with “slot 1” selectors:
```css
div .name {} /* 0 0 1 1 */
a[href$='.pdf'] {} /* 0 0 1 1 */
.pictures img:hover {} /* 0 0 2 1 */
```
- “Slot 3” holds the most important thing that can affect your CSS specificity in a CSS file: the `id`.
- Every element can have an `id` attribute assigned, and we can use that in our stylesheet to target the element.
```css
#name {} /* 0 1 0 0 */
.user #name {} /* 0 1 1 0 */
#name span {} /* 0 1 0 1 */
```
- “Slot 4” is affected by inline styles. Inline styles are CSS rules defined in the HTML itself, using the `style` attribute.
- Any inline style will have precedence over any rule defined in an external CSS file, or inside the style tag in the page header.
```css
<p style="color: red">Test</p> /* 1 0 0 0 */
```
- Even if another rule in the CSS defines the color, this inline style rule is going to be applied.
- Except for one case - if `!important` is used, which fills “slot 5”

### A note on `!important`
- Specificity does not matter if a rule ends with !important:
```css
p {
  font-size: 20px !important;
}
```
- Adding !important in a CSS rule is going to make that rule be more important than any other rule, according to the specificity rules.
- The only way another rule can take precedence is to have !important as well, and have higher specificity in the other less important slots.

## Units
- `px`, `em`, `rem`
- `px` means pixel and is one kind of unit. The most widely used measurement unit.
- `em` is the value assigned to that element’s `font-size` property, therefore its exact value changes between elements. It does not change depending on the font used, just on the font size.
- In typography, this measures the width of the `m` letter.
- `rem` is similar to `em`, but instead of varying the current element font size, it uses the root element (`html`) font size.
- You set that font size once, and `rem` will be a consistent measure across the page. It allows you to scale up/down everything by changing the font size of the root element.
- percentages let you specify values in percentages of that parent element’s corresponding property.
```css
.parent {
  width: 400px;
}
.child {
  width: 50%; /* = 200px */
}
```
