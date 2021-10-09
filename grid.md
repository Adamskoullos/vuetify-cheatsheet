# Layout & Grid

**Layout** >>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>

Example for a basic top nav, then the main app wrapped in the `v-main` tag:

```html
<template>
  <v-app light>
    <Navbar />>
    <v-main>
      <Nuxt />
    </v-main>
  </v-app>
</template>
```

Then within each page/component depending on what is happening:

```html
<template>
  <v-container>
    <v-row class="max-width mx-auto">
      <v-col> </v-col>
    </v-row>
  </v-container>
  <template> </template
></template>
```

**Breakpoints** >>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>

- `xs` > **<600px**
- `sm` > **600px - 960px**
- `md` > **960px - 1264px**
- `lg` > **1264px - 1904px**
- `xl` > **>1904px**

**Grid**: >>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>

```html
<v-container>
    <v-row>
        // Ex one with classes
        <v-col class="col-md-6 offset-md-3 col-xl-4 offset-xl-4"></v-col>
        // Ex two with props
        <v-col md="6" offset-md="3" xl="4" offset-xl="4"></v-col>
    </v-row>
</container>

```

**v-container** >>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>

> Props

- `fluid`
- `id`
- `tag` > **sets the tag name**
- `fill-height`

> can also use flex classes

**v-row** >>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>

- All the flex classes apply

> Props

- `tag` > **sets the tag name**
- `no-gutters` > **removes the gutter between cols**
- `dense` > **reduces the gutter between cols**

**v-col** >>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>

- All the flex classes apply including `align-self`
- `offset-{size}-{columns}`

> Can also use props for responsiveness:

```html
<v-col cols="12" sm="6" offset-sm="3" md="8" offset-md="2"></v-col>
```

**v-spacer** Used in between elements to push them out
