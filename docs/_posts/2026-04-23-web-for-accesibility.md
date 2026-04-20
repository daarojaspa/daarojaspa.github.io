---
category: Software
--- 
I want to start by saying: PLEASE STOP USING <DIV> FOR EVERYTHING, CSS DOESN'T REALLY FIX IT. Oh, you have no idea what CSS and div are? Stay tuned, and if you do, you may also want to stay.

The way I understand the web is a bunch of databases with interfaces made for humans, so we can interact with those databases. It makes sharing ideas, services, and daily life bureaucracy easier, so much so that now not having access to it puts you in a big disadvantage. Now, a lot of people pay for their internet connection, have their device to access it, and still can't access the knowledge or the services, and it is because the developer did not know how to create a good interface, so they made a beautiful render that was useless for these people, people with mobility problems, vision problems, or just with no mouse and only keyboard to navigate, to name a few.

## Structuring complex ideas to communicate effectively

That's the purpose of HTML5, a markup language that has a lot of semantic tags that allow the browser to make a structured hierarchy of what is going to be on the screen. It has a lot of tags to identify all the elements you could have: button tags, section tags, links, lists, headings, images, forms, and much more semantic tags that give attributes and functionality to everything you want to put in those categories. If your interface is organized, meaningful, and easy to navigate with keyboards and other devices, imagine all the work that building that infrastructure took for the developers of HTML5, for you to go and take a non-semantic tag and use it for everything (that will be a <div>). The reality is that if you use semantic HTML, at least 40% of accessibility issues will never exist.

Other 20% will be fixed if you put meaningful text inside the tags and the attributes of the tags. Images have an attribute called alt text, fill it with something that communicates what you wanted to communicate with the image, this is the challenge, not only fill it with whatever, and hide images that are purely decorative from the focus (what allows you to navigate a web page using tab or a screen reader); buttons should have text that explains what they will do when pushed, and links should have text that communicates what the link is about, a URL can be painful to hear when a screen reader is used .
## Now lets put a looks  in the structure without using a basuka 
CSS is another language that allows you to style that HTML. Communicating things only with color is a bad idea (color-blind people will not get it), but styling text so it looks like a heading when the HTML is not a heading, or communicating something using the visual flow of the information that does not respect the tab order of the keyboard, that is misleading and awful for a lot of people. CSS is amazing (I don't really like it) for a lot of things, but you can destroy accessibility with it, so these are important concepts to understand so you don't break it.

It has a box model where every element is a box with content, padding, border, and margin. These boxes, the main issue with CSS is to position and layout all these boxes in a way the format not only looks good but makes the information more understandable for visual, again without damaging accessibility for non-visual. You can create a set of rules for different elements or group of elements using specificity selectors and that the hierarchy on how those selectors get picked is top to bottom in the style sheet.

The rules or properties that control positioning and layout are the following:

DISPLAY:

block: a new line on the screen for each element, takes as much horizontal as it can
inline: never a new line for each element, only takes as much horizontal as it needs, width and height do not exist here
inline-block: inline with height and width
grid: the idea is that you divide the available space of the container into a grid, deciding how many columns and rows, inside that grid you can make elements take more than one cell at a time, so at the most basic template you can imagine a numpad-like grid (yes, you can define gaps between the cells)
flex: automatically a two-axis system is used to divide the container available space, you can change the main axis to vertical with the flex axis property

justify-content will align the items across the main axis and align-items will do it in the secondary axis, I think from an axis, but only visually, so if a user uses keyboard focus to navigate the content or screen readers, and the meaning of the information depends on the order you set visually with flexbox, well Houston, we got a problem.

POSITION:

relative to where it should be by default
fixed: will follow the user
sticky: will follow the user from a particular position

Queries are for applying certain styles depending which device you are on using the size of the screen, whatever you do the information and usability has to be accessible, does not matter if you are on a mobile or a PC.
##  Lights in to the engine 
We have not talked much about it, but the browser is a very sharp piece of software that creates object models from these files (like hierarchy trees), overlaps them and renders them, creating a render domain object that is the representation of both. After this, the layout of each of the elements in the page has to be calculated, a demanding task, and it has to be done every time you change font sizes, add or remove elements from the DOM, changing sizes or box model properties, and then is the repainting that is triggered by the change of all properties that are not layout-oriented, less expensive but still needed to have in account when CSS animations are used.

Why is this important? Well, because all this is triggered when JS enters the picture to dynamically create and inject HTML into your page.

An event is an action by the user on the page: click, enter, spacebar, a particular key. If you use events that are multi-device (activated by the mouse or the keyboard or other device), everything goes great, when you don't, well no accessibility, right?
## Just FOCUS
Components are this kind of personalized HTML tags that are crafted by wrapping HTML and CSS in JS code, and all accessibility stuff we saw earlier on CSS and HTML are really importand when building them , but if you don't correctly expose properly the semantics,  component accessibility breaks. By the way, developer, don't access innerHTML, use innerText, so you are not exposed to XSS attacks.

All frameworks are component-based, React being the most accessible I know of. You can also use dynamic updates to a page using JS, like when you committed an error filling a form and an error message appears below the field, make sure that update is announced by the screen reader. But remember about re-rendering pages DOM when we manipulate the tree with JS? Well, this can cause the focus to be lost, so avoid unnecessary changes to the DOM, and ALWAYS BE AWARE OF MANAGING FOCUS. If a modal appears in the page but is not announced and the focus is not moved to it, it is a ghost, can't be perceived or interacted with as you intended in the moment you intended.

That will be all for today. You may go to recess and play accesible games with your friends, made with propper HTML5 CSS and focus management.