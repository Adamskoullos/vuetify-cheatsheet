# Forms

Example of a login form within a card:

```html
<v-container>
  <v-row class="max-width mx-auto">
    <v-col>
      <v-card>
        <v-card-title>Login</v-card-title>
        <v-card-subtitle>Subtitle</v-card-subtitle>
        <v-card-text>
          <v-form @submit.prevent="handleLogin">
            <v-text-field label="Email" prepend-icon="mdi-account-circle" />
            <v-text-field
              label="Password"
              :type="showPass ? 'text' : 'password'"
              prepend-icon="mdi-lock"
              append-icon="showPass ? mdi-eye : mdi-eye-off"
              @click:append="showPass = !showPass"
            />
            <v-btn>Login</v-btn>
          </v-form>
        </v-card-text>
      </v-card>
    </v-col>
  </v-row>
</v-container>
```

---

**`v-form`**:

> Props

- `disabled` > disables all children
- `lazy-validation` > true unless visible validation errors
- `readonly` > all children in read only state
- `value` > boolean, validity of the form

> Functions

- `reset` > resets all inputs
- `resetValidation` > resets validation on all inputs without modifying their state
- `validate` > returns true or false

> Events

- `input` > boolean: the updated bound model
- `submit` > emitted when form is submitted

---

**`v-text-field`**: > input element

```html
<v-text-field
  v-model="name"
  :counter="10"
  :rules="nameRules"
  label="Name"
  required
></v-text-field>
```

> Props

- `append-icon`
- `append-outer-icon`
- `prepend-icon`
- `prepend-inner-icon`
- `auto-focus`
- `background-color`
- `clear-icon`
- `clearable`
- `counter` > creates a counter for the input length
- `counter-value`
- `disabled`
- `filled`
- `flat`
- `full-width`
- `height`
- `hide-details="auto"` > shows hints, counter value and validation errors if they exist
- `hide-spin-buttons` > hide spin buttons on the input when type is set to number
- `hint`
- `loader-height`
- `messages`
- `outlined`
- `readonly`
- `reverse`
- `rounded`
- **`rules`** > `:rules="nameRules"` > in the script:

```js
nameRules: [
  (v) => !!v || "Name is required",
  (v) => (v && v.length <= 10) || "Name must be less than 10 characters",
];
```

- `shaped`
- `single-line` > label does not move on focus
- `solo`
- `solo-inverted` . reduces the opacity until focused
- `success` > puts the element in success state
- `success-messages` > puts in success state and displays passed in message
- `suffix` > displays suffix text
- `validate-on-blur` > delays validation until blur event
- `value`

> Events

- `blur` > emitted when input is blurred
- `change`
- `click`
- `click:append` > when appended icon is clicked
- `click:append-outer`
- `click:clear` > when clearable icon is clicked
- `click:prepend`
- `click:prepend-inner`
- `focus`
- `input`
- `keydown`
- `mousedown`
- `mouseup`
- `update:error`

---

**`v-select`**: > drop-down

```html
<v-select
  v-model="select"
  :items="items"
  :rules="[v => !!v || 'Item is required']"
  label="Item"
  required
></v-select>
```

```js
select: null,
items: [
  'Item 1',
  'Item 2',
  'Item 3',
  'Item 4',
],
```

> Props

- `append-icon`
- `append-outer-icon`
- `prepend-icon`
- `prepend-inner-icon`
- `attach`
- `autofocus`
- `background-color`
- `cache-items`
- `chips`
- `clear-icon`
- `clearable`
- `counter`
- `counter-value`
- `deletable-chips`
- `disable-lookup`
- `disabled`
- `eager`
- `error`
- `error-count`
- `error-messages`
- `filled`
- `flat`
- `full-width`
- `height`
- `hide-details`
- `hide-selected`
- `hide-spin-buttons`
- `hint`
- `item-color`
- `item-disabled`
- `item-text`
- `item-value`
- **`items`** > an array of items, can be array of strings or objects:

```js
{
  text: string | number | object,
  value: string | number | object,
  disabled: boolean,
  divider: boolean,
  header: string
}
```

- `loading`
- `menu-props`
- `messages`
- `multiple`
- `no-data-text`
- `open-on-clear`
- `outlined`
- `placeholder`
- `prefix`
- `readonly`
- `return-object`
- `revers`
- `rounded`
- **`rules`**
- `shaped`
- `single-line`
- `small-chips`
- `solo`
- `solo-inverted`
- `success`
- `success-messages`
- `suffix`
- `validate-on-blur`
- `value`
- `value-comparator`

> Events

- `blur` > emitted when input is blurred
- `change`
- `click`
- `click:append` > when appended icon is clicked
- `click:append-outer`
- `click:clear` > when clearable icon is clicked
- `click:prepend`
- `click:prepend-inner`
- `focus`
- `input`
- `keydown`
- `mousedown`
- `mouseup`
- `update:error`
- `update:list-index` > when menu item is selected using keyboard arrows
- `update:search-input`

---

**`v-radio`**:

**`v-radio-group`**:

---

**`v-checkbox`**:

**`v-simple-checkbox`**:
