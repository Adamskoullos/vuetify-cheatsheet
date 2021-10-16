# Buttons

- `v-btn-toggle` > group a list of buttons
- `v-btn` > Individual button
- `Floating Actions Buttons` > `fab`

---

**`v-btn-toggle`**:

- `active-class`
- `background-color`
- `borderless` > removes the groups border
- `color`
- `dark`
- `dense` > reduces the size and padding
- `group` > removes bg-color, border and increases space between buttons
- `light`
- `mandatory`
- `max`
- `multiple`
- `rounded`
- `shaped`
- `tile` > remove border-radius

---

**`v-btn`**:

- `absolute` > overides `app` position: fixed
- `block` > full width
- `bottom` > aligns component towards the bottom
- `color`
- `dark`
- `depressed` > removes box-shadow
- `disabled`
- `elavation` > box-shadow between 1-24
- `exact` > Prop: to only highlight when exact route is active
- `exact-active-class` > use to configure class for active tab
- `fab` > floating-action-button (circle)
- `fixed`
- `href`
- `icon` > button becomes round and the `text` prop is added
- `input-value` > controls buttons active state
- `large`
- `left` > position
- `light`
- `link` > this is added if the button has `to` or `href`
- `loading` > adds a loading icon animation `:loading="loading1"` (1-5)
- `max-height`
- `max-width`
- `min-height`
- `min-width`
- `nuxt` > specifies the lik is a `NuxtLink`
- `outlined` > transparent backgorund + boarder
- `retain-focus-on-click`
- `right`
- `ripple` > applies the v-ripple directive
- `rounded` > border-radius
- `shaped` > border-radius on top left and bottom right
- `small`
- `tag`
- `title` > removes border-radius
- `top` > aligns component to the top
- `value` > visible or hidden
- `width`
- `x-large`
- `x-small`

---

**`fab`** > the fab prop turns buttons round and are great for icon buttons:

- `elevation`
- `icon` > removes background color
- `outlined` > removes background color and adds an outline
- `text` > removes background
- `tile` > background changes from circle to square

**`v-fab-transition`** tags surround a fab `v-btn` and provide a nice transition as the component is shown via a boolean data property

**`v-speed-dial`** > a cool drop down component for fab buttons

- `top`
- `bottom`
- `right`
- `left`
- `fixed`
- `absolute`
- `mode` > if useing Vue transitions `out-in`, `in-out`
- `open-one-hover`
- `origin` > the point of anchor for the transition, good for rotational transitions, `center`, `bottom`, `top`, `left`, `right`
- `transition` > able to set the transition from either the built in options or custom
