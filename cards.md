# Cards

Basic structure:

```html
<v-card>
  <v-card-title> Tile </v-card-title>
  <v-card-subtitle> Subtitle </v-card-subtitle>
  <v-card-text> Some text </v-card-text>
  <v-card-actions> combination of elements </v-card-actions>
</v-card>
```

Example:

```html
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
```
