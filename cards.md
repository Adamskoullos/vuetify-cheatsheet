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
  <v-card-title> Tile </v-card-title>
  <v-card-subtitle> Subtitle </v-card-subtitle>
  <v-card-text>
    <p>Login</p>
    <v-text-field label="name" />
    <v-text-field label="email" />
    <v-btn @click="handleLogin">Login</v-btn>
  </v-card-text>
  <v-card-actions> combination of elements </v-card-actions>
</v-card>
```
