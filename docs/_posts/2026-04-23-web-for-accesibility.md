---
category: Software
--- 
I want to start by saying: PLEASE STOP USING `<div>` FOR EVERYTHING — CSS DOESN'T REALLY FIX IT. Oh, you have no idea what CSS and `<div>` are? Stay tuned. And if you do, you may also want to stay.

The way I understand the web is: a bunch of databases with interfaces made for humans, so we can interact with those databases. It makes sharing ideas, services, and daily-life bureaucracy easier — so much so that now not having access to it puts you at a big disadvantage. A lot of people pay for their internet connection, have their device to access it, and still can't access the knowledge or the services. And it is because the developer did not know how to create a good interface, so they made a beautiful render that was useless for these people: people with mobility problems, vision problems, or just with no mouse and only a keyboard to navigate, to name a few.

## Structuring complex ideas to communicate effectively

That's the purpose of HTML5: a markup language with a lot of semantic tags that allow the browser to build a structured hierarchy of what is going to be on the screen. It has tags to identify all the elements you could have — button tags, section tags, links, lists, headings, images, forms, and many more semantic tags that give attributes and functionality to everything you want to put in those categories. If your interface is organized, meaningful, and easy to navigate with keyboards and other devices… imagine all the work that building that infrastructure took for the developers of HTML5, for you to go and take a non-semantic tag and use it for everything (that would be a `<div>`). The reality is that if you use semantic HTML, at least 40% of accessibility issues will never exist.

Another 20% will be fixed if you put meaningful text inside the tags and the attributes of the tags. Images have an attribute called alt tex, fill it with something that communicates what you wanted to communicate with the image. That is the challenge: not just filling it with whatever. And hide purely decorative images from the focus (what allows you to navigate a web page using tab or a screen reader). Buttons should have text that explains what they will do when pushed, and links should have text that communicates what the link is about — a URL can be painful to hear when a screen reader reads it.

## Now let's put a look on the structure without using a bazooka

CSS is another language that allows you to style that HTML. Communicating things only with color is a bad idea (color-blind people will not get it). Styling text so it looks like a heading when the HTML is not a heading, or communicating something using a visual flow of information that does not respect the tab order of the keyboard — that is misleading and awful for a lot of people. CSS is amazing (I don't really like it) for a lot of things, but you can destroy accessibility with it, so these are important concepts to understand so you don't break it.

It has a box model where every element is a box with content, padding, border, and margin. The main issue with CSS is to position and lay out all these boxes in a way that not only looks good but makes the information more understandable visually — again, without damaging accessibility for non-visual users. You can create a set of rules for different elements or groups of elements using specificity selectors, and the hierarchy of how those selectors get picked is top to bottom in the style sheet.

The rules or properties that control positioning and layout are the following:

**DISPLAY:**

- `block`: a new line on the screen for each element; takes as much horizontal space as it can.
- `inline`: never a new line for each element; only takes as much horizontal space as it needs. Width and height do not exist here.
- `inline-block`: inline, with height and width.
- `grid`: the idea is that you divide the available space of the container into a grid, deciding how many columns and rows. Inside that grid you can make elements take more than one cell at a time, so at the most basic template you can imagine a numpad-like grid (yes, you can define gaps between the cells).
- `flex`: automatically a two-axis system is used to divide the container's available space. You can change the main axis to vertical with the `flex-direction` property.

`justify-content` will align the items across the main axis and `align-items` will do it on the secondary axis — but only visually. So if a user uses keyboard focus to navigate the content, or screen readers, and the meaning of the information depends on the order you set visually with flexbox… well, Houston, we got a problem.

**POSITION:**

- `relative`: to where it should be by default.
- `fixed`: will follow the user.
- `sticky`: will follow the user from a particular position.

Media queries are for applying certain styles depending on which device you are on, using the size of the screen. Whatever you do, the information and usability have to be accessible — it doesn't matter if you are on a mobile or a PC.

## Lights into the engine

We have not talked much about it, but the browser is a very sharp piece of software that creates object models from these files (like hierarchy trees), overlaps them and renders them, creating a render DOM that is the representation of both. After this, the layout of each of the elements on the page has to be calculated — a demanding task — and it has to be done every time you change font sizes, add or remove elements from the DOM, or change sizes or box-model properties. Then there is the repainting, triggered by the change of all properties that are not layout-oriented: less expensive, but still worth keeping in mind when CSS animations are used.

Why is this important? Well, because all this is triggered when JS enters the picture to dynamically create and inject HTML into your page, and the result will afect the position of your screen reader and can mak information imposible to navigate. 

An event is an action by the user on the page: click, enter, spacebar, a particular key. If you use events that are multi-device (activated by the mouse or the keyboard or other devices), everything goes great. When you don't… well, no accessibility, right?

## Just FOCUS

Components are these kinds of personalized HTML tags that are crafted by wrapping HTML and CSS in JS code, and all the accessibility stuff we saw earlier on CSS and HTML is really important when building them. But if you don't properly expose the semantics, component accessibility breaks. By the way, developer: don't access `innerHTML`, use `innerText`, so you are not exposed to XSS attacks.

All frameworks are component-based, React being the most accessible I know of. You can also use dynamic updates to a page using JS — like when you committed an error filling out a form and an error message appears below the field. Make sure that update is announced by the screen reader. But remember about re-rendering the page's DOM when we manipulate the tree with JS? Well, this can cause the focus to be lost, so avoid unnecessary changes to the DOM, and ALWAYS BE AWARE OF MANAGING FOCUS. If a modal appears on the page but is not announced and the focus is not moved to it, it is a ghost — can't be perceived or interacted with as you intended in the moment you intended.

That will be all for today. You may go to recess and play accessible games with your friends, made with proper HTML5, CSS, and focus management.