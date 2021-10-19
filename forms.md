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

**`v-text-field`**:

---

**`v-select`**:

---

**`v-radio`**:

**`v-radio-group`**:

---

**`v-checkbox`**:

**`v-simple-checkbox`**:
