# Navigation

There are two main navigation structures:

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
