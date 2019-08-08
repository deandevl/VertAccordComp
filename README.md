## vert-accord-comp

**vert-accord-comp** is a Vue.js web component (version >= 2.5) that provides an accordion, expanding/contracting like display of list content.  The component is based on the article:  [Cross Browser Pure CSS3 Vertical Accordion](http://www.w3avenue.com/2010/04/02/cross-browser-pure-css3-vertical-accordion/) by Saud Khan. 

 **vert-accord-comp** can be installed via with the included `package.json` file for a local installation via the [npm install](https://docs.npmjs.com/cli/install.html "npm install") command.  **vert-accord-comp** depends on the [vue.js](https://vuejs.org/ "Vue.js") framework.  A demo folder is provided that used [Parcel](https://parceljs.org/) together with its associated `package.json` file to bundle together  **vert-accord-comp** along with its [vue.js](https://vuejs.org/ "Vue.js") dependency for a simple application.  Further details are provided below for running the demo.

## Props

A prop in Vue.js is a custom attribute for passing information from a parent component hosting **vert-accord-comp** instance(s) to an **vert-accord-comp** as a child component. 

**vert-accord-comp** has the following props for a parent to bind and send information to:

`slot_names` -- an array of strings that references the slot names in the parent template (explanation: see below) (array of string names, default: null)

`title` -- a title to be displayed above the list (string,default: null)

`content_height` --  defines the content height for the expanded item's content in units of pixels (number, default: 200)

`css_variables` -- defines the css variables for **vert-accord-comp** (object, default: null)

To create a list of expandable items you define a html template for each item that is assigned a slot name (i.e. `<template slot="...":`).  The `slot_names` array is an array of strings that references a slot name for each template that defines an item's content.  As in the following example multiple templates are defined within the **vert-accord-comp** which has the `slot_names`  array ` = ['Hammers','Screwdrivers','Knives','Wrenches','Saws']` referencing all of the template slot names 

```
      <vert-accord-comp
        title="Tool Inventory"
        :slot_names="slot_names"
        :content_height="content_height"
        :css_variables="css_variables">
        <template slot="Hammers">
          <div class="vertAccordComp_itemContent">
            Number: 11 <br>
            Types: ball pein(2), heavy(2), sludge(3), claw(4)
          </div>
        </template>
        <template slot="Screwdrivers">
          <div class="vertAccordComp_itemContent">
            Number: 41 <br>
            Types: blade(10), philips(8), mini(23)
          </div>
        </template>
        <template slot="Knives">
          <div class="vertAccordComp_itemContent">
            Number: 16 <br>
            Types: switch(4), fixed(8), putty(4)
          </div>
        </template>
        <template slot="Wrenches">
          <div class="vertAccordComp_itemContent">
            Number: 23 <br>
            Types: pipe(6), socket(12), crescent(5)
          </div>
        </template>
        <template slot="Saws">
          <div class="vertAccordComp_itemContent">
            Number: 15 <br>
            Types: hack(4), cross(3), rip(5), circular(3)
          </div>
        </template>
      </vert-accord-comp>
    </div>
  `,
  data: function() {
    return {
      slot_names:['Hammers','Screwdrivers','Knives','Wrenches','Saws'],
      content_height: 150,
      css_variables: {
        vertaccord_comp_item_width: '300px'
      }
    }
  },
```

It is important that the slot names for each template correspond to the names in the `slot_names` array.  Content defined in the templates can be any html tags or other components.  

## Styling

The **css_variables** prop is a javascript object that contains any combination of css variable names as keys and associated values.  The following list are the css variable names along with their default values for a quick styling of **vert-accord-comp**:

```
{
  vertaccord_comp_font_family: 'Verdana,serif',

  vertaccord_comp_title_color: 'black',
  vertaccord_comp_title_font_size: '18px',
  vertaccord_comp_title_font_weight: 'bold',

  vertaccord_comp_item_color: 'black',
  vertaccord_comp_item_background: 'white',
  vertaccord_comp_item_width: '200px',

  vertaccord_comp_item_title_hover_color: 'white',
  vertaccord_comp_item_title_hover_background: 'linear-gradient(to bottom, #454545 0%, #cccccc 100%)',
}
```

## Events

**vert-accord-comp** has no events.

## Demonstration

One demonstration of **vert-accord-comp**  is provided in the folder named `demo/dist` and can be viewed by hosting the `index.html`file.  The demo (templated in the `App.vue` file)  displays a list of five tools with some brief content on each one.  Initially all the content is contracted, but when you mouse over an item's title the content expands for viewing.  A mouse out from the item title contracts again the item content.

As a suggestion, install [http-server](https://www.npmjs.com/package/http-server "http-server") locally/globally via [npm](https://www.npmjs.com/ "npm") then enter the command `http-server`in the **vert-accord-comp** `dist` directory.  From a browser enter the url: `localhost:8080/` to view the demo.

