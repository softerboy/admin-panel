---
description: >-
  This page introduces how to customize and change admin panel's left sidebar
  including menu items, icons and colors etc.
---

# Sidebar

You can find **sidebar**\* specific files at **src/components/sidebar** folder.  
  
By default sidebar has three slots named **header**, **menu-item** and **footer** and each comes with default implementation.

## Setup sidebar menu items

To setup menu items in sidebar you need to dispatch vuex store's **`setMenuItems`** action with menu items array.

```javascript
/**
* @typedef { Object<string, any> } MenuItem
* @property { string } text Displayable text of menu item
* @property { number|string } [id] An unique id of menu item. This id 
*                used for vue internal foreach loop as :key
*                For more information @see https://vuejs.org/v2/guide/list.html#key
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
      text: "Inner item 2"
  }, {
      id: 3,
      text: "Inner item 3"
  }]
}

store.dispatch('sidebar/setMenuItems', menuItems)
```

