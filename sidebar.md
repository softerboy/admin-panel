---
description: >-
  This page introduces how to customize and change admin panel's left sidebar
  including menu items, icons and colors etc.
---

# Sidebar

You can find **sidebar**\* specific files at **src/components/sidebar** folder.  
  
By default sidebar has three slots named **header**, **menu-item** and **footer** and each comes with default implementation.

## Setup sidebar menu items

To setup menu items in sidebar you need to dispatch vuex store's **`setMenuItems`** action with menu items array. Each array item must contain this properties:

* **text** -  ****{ string } ****displayable text of menu item
* **id** - { string \| number } an optional unique id of menu item. This id used for Vue's internal        foreach loop as **:key** prop for optimize list rendering. I you don't provide it default will be generated. See [https://vuejs.org/v2/guide/list.html\#key](https://vuejs.org/v2/guide/list.html#key) for more information

```javascript
/**
* @typedef { Object<string, any> } MenuItem
* @property { string } text Displayable text of menu item
* @property { number|string } [id] An unique id of menu item. This id 
*            used for vue internal foreach loop as :key prop for optimize list rendering.
*            This propr
*            For more information @see https://vuejs.org/v2/guide/list.html#key
* @property { string } icon A name of icon
* @property { MenuItem[] } Child/sub menu items of that item. 
                           This will display collapsable menu items
*/

const menuItems = [{
  text: "Dashboard",
  id: 1,
  icon: "home",
  children: [{
      id: "1",
      text: "Inner item 1"
  }, {
      id: 2,
      text: "Inner item 2",
      onClick(item) {
          console.log(`${item.text} clikced`)
      }
  }, {
      id: 3,
      text: "Inner item 3"
  }]
}

this.$store.dispatch('sidebar/setMenuItems', menuItems)
```

