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

## Form

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

## Text Input

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

## Select

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
- `attach` > specifies which DOM element that this component should detach to
- `autofocus`
- `background-color`
- `cache-items` > keeps a local unique copy of all items that have been passed through the items prop
- `chips` > changes display of selections to chips
- `clear-icon`
- `clearable`
- `counter` > creates counter for input length (default 25)
- `counter-value`
- `deletable-chips` > adds a remove icon to selected chips
- `disable-lookup`
- `disabled`
- `eager` > force the components content to render on mounted
- `error` > puts the input in a manual error state
- `error-count` > total number of errors that should display at once
- `error-messages` > Puts the input in an error state and passes through custom error messages
- `filled` > filled input style
- `flat` > removes elevation
- `full-width`
- `height`
- `hide-details`
- `hide-selected`
- `hide-spin-buttons`
- `hint` > hint text
- `item-color` > color of selected items
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

- `loading` > displays linear progress bar
- `menu-props` > pass props through to the v-menu component
- `messages` > displays a list of messages or message if using a string
- `multiple` > changes select to multiple, accepts array for value
- `no-data-text` > display text whe there is no data
- `open-on-clear`
- `outlined`
- `placeholder`
- `prefix` > displays prefix text
- `readonly`
- `return-object`
- `revers`
- `rounded`
- **`rules`**
- `shaped`
- `single-line` > label does not move on focus
- `small-chips`
- `solo` > changes the style of the input
- `solo-inverted` > reduces the opacity until focused
- `success` > puts in success state
- `success-messages` puts in success state and passes in success messages
- `suffix` > displays suffix text
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

## Radio

The `V-model` in the `v-radio-group` holds the `value` of the checked radio. In the below example `1` is set as the default, which is the value of the first radio.

```html
<v-radio-group v-model="radioGroup">
  <v-radio v-for="n in 3" :key="n" :label="`Radio ${n}`" :value="n"></v-radio>
</v-radio-group>
```

```js
<script>
  export default {
    data () {
      return {
        radioGroup: 1,
      }
    },
  }
</script>

```

**`v-radio-group`**:

> Props

`v-radio-group` has many of the standard input props as well as:

- `active-class` > applies active class to children when they are active
- `max` > sets maximum number of selections that can be made
- `multiple` > allows multiple selected items, value prop must be an array
- `row` > displays in row

> Events

- `change`
- `click:append` > when appended icon is clicked
- `click:prepend`
- `mousedown`
- `mouseup`
- `update:error`

**`v-radio`**:

> Props

- `active-class`
- `off-icon` > the icon used when inactive
- `on-icon` > icon used when active
- `ripple`

> Events

- `change`
- `click`
- `click:append` > when appended icon is clicked
- `click:prepend`
- `mousedown`
- `mouseup`
- `update:error`

---

## Checkbox

A single checkbox with its own v-model data property uses true and false as its value:

```html
<template>
  <v-container fluid>
    <v-checkbox
      v-model="checkbox1"
      :label="`Checkbox 1: ${checkbox1.toString()}`"
    ></v-checkbox>
    <v-checkbox
      v-model="checkbox2"
      :label="`Checkbox 2: ${checkbox2.toString()}`"
    ></v-checkbox>
  </v-container>
</template>
```

```js
<script>
  export default {
    data () {
      return {
        checkbox1: true,
        checkbox2: false,
      }
    },
  }
</script>
```

Multiple checkboxes using the same v-model data property `selected` which is an array so as to allow for multiple selections:

```html
<template>
  <v-container fluid>
    <p>{{ selected }}</p>
    <v-checkbox v-model="selected" label="John" value="John"></v-checkbox>
    <v-checkbox v-model="selected" label="Jacob" value="Jacob"></v-checkbox>
  </v-container>
</template>
```

```js
<script>
  export default {
    data () {
      return {
        selected: ['John'],
      }
    },
  }
</script>
```

---

## Autocomplete

---

## Rules and Validation
