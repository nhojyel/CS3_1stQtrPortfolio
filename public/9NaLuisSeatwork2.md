# Seatwork #2 - Getting to know CSS Position and z-index.
### This seatwork will ask you to implement the different CSS position on a given code.
### short link to this .md file is: https://bit.ly/4c61P9K
#### Resources (also found in Khub week 5)
- [4 Minute Youtube Video on CSS Position](https://www.youtube.com/watch?v=YEmdHbQBCSQ)
- [CSS Position Tutorial](https://roycan.github.io/CssPositioningZIndexLab/)

### Instructions: 
1. This is individual submission in khub, but you can work with a partner.  When you submit in khub please place both your names in the submission bin.
2. Guided Activity (30 minutes), please follow what is being required.  

    - Make a copy of this .md file to your Q4 repository and name it as **SectionLNseatwork2.md** example **9LiCruzSeatwork2.md**. Place it in your q4 repository vscode local computer. Committing frequently to your Github repository.  
    - Copy the code below and paste it inside a new file (name it as SectionLNseatwork2.html). Place this file in the same location where the .md file is saved. 
    - Change the content values of the meta tags to your names for author/s and the date today for revised.
    - Please do the following tasks that will ask you to reposition HTML elements then answer the guided question for each task on the .md file. Commit changes to the .md file and to the .html file as well.
    **- This seatwork is worth 20pts and should be submitted by the end of the period** The link to [KHub submission bin](https://khub.mc.pshs.edu.ph/mod/assign/view.php?id=15481).
      - Submit the links to your .md file and .html file.

```html
<!DOCTYPE html>
<html>
<head>
  <meta name="author" content="<your names>" />
  <meta name="revised" content="<date today>" />
  <style>
    body { font-family: Arial, sans-serif; }
    .header, .footer {
      background: lightblue;
      padding: 10px;
    }
    .footer {
       opacity: 0.5;
    }
    .sidebar {
      background: lightgreen;
      width: 150px;
      height: 200px;
    }
    .content {
      background: lightyellow;
      width: 300px;
      height: 200px;
    }    
  </style>
</head>
<body>
  <div class="header">Header</div>
  <div class="sidebar">Sidebar</div>
  <div class="content">Main Content</div>
  <div class="footer">Footer</div>
</body>
</html>
```
### Step 1 (Static vs Relative):

- Add in css ```position: relative; top: 20px; left: 20px;``` to .sidebar.

- Guided Question: What changed compared to the default static positioning? Try to give different values to top and left or you can change it to bottom, right.

- My Answer: With static positioning, the sidebar sits exactly where the browser places it in the normal document flow, you cannot move it with top, left, bottom, or right. Once I switched to relative positioning, the element shifts visually from where it originally was, original space is still reserved and other elements don't collapse into the gap. If I changed the top to 20px to 80px, the sidebar moves further down, switching to bottom: 20px pushes it upwards instead. 

### Step 2 (Fixed):

- Add in css ```position: fixed; bottom: 0; width: 100%;``` to .footer.

- Guided Question: What happens when you scroll the page? Why does the footer behave differently from position relative?

- My Answer: When I scroll the page, the footer stays glued to the bottom of the screen, it never moves. This is because a fixed positioning positions the element relative to the viewport, not the document. Relative positioning on the other hand, is still part of the normal page flow, so it scrolls along with everything else. Fixed elements are also completely removed from the document flow, meaning other elements don't reserve space for them.

### Step 3 (Absolute):

- Add in css ```position: absolute; top: 66px; left: 200px;``` to .content.

- Guided Question: What is the effect of position: absolute on an element? How is it different from fixed?

- My Answer: Absolute positioning removes the element from the normal document flow (just like fixed) and places it at exact coordinates, but those coordinates are measured from its nearest positioned ancestor. If no such parent exists, it defaults to the body. The critical difference from fixed is that an absolute element scrolls with the page, anchored to a point in the document, not to the viewport. So when I scroll down, an absolute element disappears from the top; a fixed element never does.


### Step 4 : (Absolute)

- Add in html ```<div class="notice">Notice!</div>``` and include the css below:

```css
.notice {
    position: absolute;
    top: 60px;
    left: 400px;
    background: orange;
    padding: 10px;
    z-index: 2;
}
```

- Give .content a z-index: 1.

- Guided Question: Why does the notice appear on top of the content? What happens if you swap the z‑index values?

- My Answer: Z-index controls the stacking order along the Z-axis (depth). A higher value means the element is rendered closer to the viewer, on top of elements with lower values. Since .notice has a z-index of 2 and .content having an index of 1, the notice wins and appears on top. If I swap them their indices, the content box would cover the notice instead. Although, z-index only works on elements that have a position value other than static. 

- Challenge: 
    * What changes that you have to do on the code that will position .notice box on the top right corner of the .content box? Please write the code on paper as well (both html and css on the part of .notice and .content). 

    - My answer: To make .notice appear on the top right corner of .content, I made .content as the positioned ancestor by giving it a relative positon (position:relative). Then, I gave.notice absolute positioning (position:absolute) with top:0 and right:0, which snaps it to the top right corner of .content. 


    * Try to change the position of .content to relative then to fixed. What do you observed each time?

    - My answer: When .content is set to relative, it stays in the normal document flow, scrolls with the page, and becomes the anchor point of .notice if nested inside it. When changed to fixed, it is pulled out of the flow entirely, surrouding elements  reflow as if it doesn't exist, and it locks to the viewport, staying frozen on screen regardless of scrolling. 

    * What do you observe on about the effect of z-index on .notice and .content boxes?

    - My answer: The z-index property controls which 2 elements overlap with .notice at 2 and .content at 1, the notice renders above the content box, as it has the higher index, but swapping these values would cause the content box to cover the notice instead. As mentioned earlier, I noticed that z-index only works when the element has a positon value other than static. Without it, the browswer ignores the z-index entirely and falls back to the default HTML source order for stacking. 

3. Please answer the following reflection questions (15 minutes)

    a. Could you summarize the differences between the CSS position values (static, relative, absolute, fixed)? 

    - Static is the default value where the element simply follows the normal document flow and cannot be moved using offset properties like top or left. Relative keeps the element in the flow but allows you to visually nudge it from its original spot, while its original space is still reserved. Absolute removes the element from the flow entirely and positions it relative to its nearest non-static ancestor, or the body if none exists. Fixed also removes the element from the flow but anchors it to the viewport instead, meaning it stays in the same spot on screen even when the user scrolls.

    b. How does absolute positioning depend on its parent element?

    - An absolutely positioned element depends on its parent because it uses the parent as its reference point for placemen, meaning its top, left, right, bottom values are measured from the parent's edges, not the page. However, this only works if the parent has a position value other than static. If the parent is just static, the absolutely positioned child ignores it and looks further up for another positioned ancestor, or falls all the way back to the body. This is why giving a parent relative positioning is so important as it makes the parent the anchor, ensuring the child is positioned relative to it and not somewhere unexpected on the page.

    c. How do you differentiate sticky from fixed (you can research on sticky)?

    - Both sticky and fixed keep an element visible on screen while scrolling, but they behave differently. Fixed locks the element to the viewport immediately from the moment the page loads, meaning it is always visible no matter where the user scrolls. Sticky on the other hand, starts out scrolling normally with the page like a regular element, but once it reaches a defined threshold such as top: 0 it sticks in place. In short,  is that a sticky element only stays stuck while its parent container is still in view.

    d. If you were designing a webpage for a school event, how might you use positioning to highlight important information? Please give concrete examples.

    - For example, in next year's ALAB Week, since it is our school's opening week filled with academic events, club showcases, and food booths ,  I would create a website for it. A fixed announcement bar at the top could display "ALAB Week - This Saturday, July 30" so visitors always see the date no matter how far they scroll. Club and food booth images could have absolutely positioned badges like "Free to Join!" will be overlaid on their corners to catch students' attention. Finally, sticky positioning could be applied to category headers like Academics, Clubs, and Food so they stay visible as students browse through each section of the page.