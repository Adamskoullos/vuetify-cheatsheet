# Navigation

There are two main navigation wrapping tags:

**v-app-bar** Used for an applications main navigation and fully featured

**v-toolbar** Used for mini controls within pages and components similar to above but lacks some features

Features that only the `v-app-bar` has:

- `app` > **prop used to designate component as part of the layout**
- `clipped-left` > **positions the** `v-navigation-drawer` **below the** `app-bar`
- `clipped-right` > **same as above, but for drawers on the right**
- `value` > **controls whether component is visible or hidden**

> Scroll Animations

- `collapse-on-scroll`
- `elevate-on-scroll`
- `fade-img-on-scroll`
- `hide-on-scroll`
- `inverted-on-scroll`
- `scroll-off-screen`
- `scroll-target`
- `scroll-threshold`
- `shrink-on-scroll`

Features that `v-app-bar` & `v-toolbar` have:

- `absolute` > **positions absolute**
- `bottom` > **aligns component towards the bottom**
- `collapse`
- `color`
- `dark` > **theme**
- `dense` > **reduces the height of the content to 48px (96px with prominent prop)**
- `elevation` > **adds a box-shadow from 0-24**
- `extended` > **Extend the height of the component**
- `extension-height` > **specify height for** `extension slot`
- `flat` > **removes box-shadow**
- `floating` > **applies display: inline-flex**
- `height` > **add specific height**
- `light` > **theme**
- `max-height`
- `min-height`
- `max-width`
- `min-width`
- `outlined` > **removes box-shadow and adds border**
- `prominent` > **increase content to 128px**
- `rounded` > **class:**
  - `rounded-0`
  - `rounded-sm`
  - `rounded-md`
  - `rounded-lg`
  - `rounded-xl`
  - `rounded-pill`
  - `rounded-circle`
- `shaped` > **adds border-radius to top-left and bottom-right**
- `short` > **reduce height of content to 56px (112px with prominent)**
- `src`
- `tile` > **removes border-radius**
- `width`

---

Inside **v-app-bar** and **v-toolbar** we use the same internal components:

- **`v-toolbar-title`** > Logo

- **`v-spacer`**

- **`v-toolbar-items`** > This houses all navigation items:
  - `v-btn`
  - `v-icon`

---

**v-navigation-drawer**:

---

Example:

```html
<template>
  <div>
    <v-app-bar>
      <v-toolbar-title>Logo</v-toolbar-title>
      <v-spacer></v-spacer>
      <!-- Mobile burger button to open drawer menu-->
      <span class="hidden-sm-and-up">
        <v-btn @click.stop="drawer = !drawer">
          <v-icon>some-icon</v-icon>
        </v-btn>
      </span>
      <!-- Main nav bar -->
      <v-toolbar-items>
        <v-btn :to="/one" text>
          <v-icon small left>some-icon</v-icon>
          Page One
        </v-btn>
        <v-btn :to="/two" text>
          <v-icon small left>some-icon</v-icon>
          Page Two
        </v-btn>
      </v-toolbar-items>
    </v-app-bar>
    <!-- Navigation drawer for mobile screens -->
    <v-navigation-drawer v-model="drawer" absolute temporary right>
      <v-list>
        <v-list-item
          v-for="item in items"
          :key="item.title"
          :to="item.link"
          link
        >
          <V-list-item-icon>
            <v-icon>fa-{{ item.icon }}</v-icon>
          </V-list-item-icon>
          {{ item.title }}
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
  </div>
</template>
```

Then in the script we add the `drawer` and `items` properties:

```js
data(){
  return{
    drawer: false,
    items: [
      {title: 'One', link: 'one', icon: 'some-icon'},
      {title: 'Two', link: 'two', icon: 'some-icon'}
    ]
  }
}
```
