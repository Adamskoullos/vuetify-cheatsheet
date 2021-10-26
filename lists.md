# Lists

- [v-list](#v-list)
- [v-list-group](#v-list-group)
- [v-list-item](#v-list-item)
- [v-list-item-action](#v-list-item-action)
- [v-list-item-action-text](#v-list-item-action-text)
- [v-list-item-avatar](#v-list-item-avatar)
- [v-list-item-content](#v-list-item-content)
- [v-list-item-group](#v-list-item-group)
- [v-list-item-subtitle](#v-list-item-subtitle)
- [v-list-item-title](#v-list-item-title)

---

## v-list

`v-list` elements are list containers

```html
<v-list dense>
  <v-subheader>REPORTS</v-subheader>
  <v-list-item-group v-model="selectedItem" color="primary">
    <v-list-item v-for="(item, i) in items" :key="i">
      <v-list-item-icon>
        <v-icon v-text="item.icon"></v-icon>
      </v-list-item-icon>
      <v-list-item-content>
        <v-list-item-title v-text="item.text"></v-list-item-title>
      </v-list-item-content>
    </v-list-item>
  </v-list-item-group>
</v-list>
```

```js
data: () => ({
    selectedItem: 1,
    items: [
    { text: 'Real-Time', icon: 'mdi-clock' },
    { text: 'Audience', icon: 'mdi-account' },
    { text: 'Conversions', icon: 'mdi-flag' },
    ],
}),

```

---

## v-list-group

`v-list-group` elements wrap sub-groups for nested lists. The example below has the `Users` tab as the main group drop down, then within here there are two further `list-groups` which are nested drop downs:

![Screenshot from 2021-10-26 07-36-15](https://user-images.githubusercontent.com/73107656/138821850-89d32bbf-b88e-41d9-90b6-ec1bf42afdfc.png)

```html
<template>
  <v-card class="mx-auto" width="300">
    <v-list>
      <v-list-item>
        <v-list-item-icon>
          <v-icon>mdi-home</v-icon>
        </v-list-item-icon>

        <v-list-item-title>Home</v-list-item-title>
      </v-list-item>
      <!-- Main User group drop down ------------------------------------ -->
      <v-list-group :value="true" prepend-icon="mdi-account-circle">
        <template v-slot:activator>
          <v-list-item-title>Users</v-list-item-title>
        </template>
        <!-- Sub-Group One ------------------------------------ -->
        <v-list-group :value="true" no-action sub-group>
          <template v-slot:activator>
            <v-list-item-content>
              <v-list-item-title>Admin</v-list-item-title>
            </v-list-item-content>
          </template>

          <v-list-item v-for="([title, icon], i) in admins" :key="i" link>
            <v-list-item-title v-text="title"></v-list-item-title>

            <v-list-item-icon>
              <v-icon v-text="icon"></v-icon>
            </v-list-item-icon>
          </v-list-item>
        </v-list-group>
        <!-- Sub-Group Two ------------------------------------ -->
        <v-list-group no-action sub-group>
          <template v-slot:activator>
            <v-list-item-content>
              <v-list-item-title>Actions</v-list-item-title>
            </v-list-item-content>
          </template>

          <v-list-item v-for="([title, icon], i) in cruds" :key="i" link>
            <v-list-item-title v-text="title"></v-list-item-title>

            <v-list-item-icon>
              <v-icon v-text="icon"></v-icon>
            </v-list-item-icon>
          </v-list-item>
        </v-list-group>
      </v-list-group>
    </v-list>
  </v-card>
</template>
```

```js
<script>
  export default {
    data: () => ({
      admins: [
        ['Management', 'mdi-account-multiple-outline'],
        ['Settings', 'mdi-cog-outline'],
      ],
      cruds: [
        ['Create', 'mdi-plus-outline'],
        ['Read', 'mdi-file-outline'],
        ['Update', 'mdi-update'],
        ['Delete', 'mdi-delete'],
      ],
    }),
  }
</script>

```

## v-list-item

The `v-list-item` tags wrap all elements for each list item and can have the prop: `teo-line` or `three-line` to style the item over a number of lines. The prop `link` can be added to turn the item into a link.

The below example shows a nice combination of `v-list-item` components within a card (not shown):

![Screenshot from 2021-10-26 07-46-50](https://user-images.githubusercontent.com/73107656/138823184-52b6f8dc-beba-4108-a026-dc1fd8d91a17.png)

```html
<v-list subheader two-line>
  <v-subheader inset>Folders</v-subheader>

  <v-list-item v-for="folder in folders" :key="folder.title">
    <v-list-item-avatar>
      <v-icon class="grey lighten-1" dark> mdi-folder </v-icon>
    </v-list-item-avatar>

    <v-list-item-content>
      <v-list-item-title v-text="folder.title"></v-list-item-title>

      <v-list-item-subtitle v-text="folder.subtitle"></v-list-item-subtitle>
    </v-list-item-content>

    <v-list-item-action>
      <v-btn icon>
        <v-icon color="grey lighten-1">mdi-information</v-icon>
      </v-btn>
    </v-list-item-action>
  </v-list-item>

  <v-divider inset></v-divider>

  <v-subheader inset>Files</v-subheader>

  <v-list-item v-for="file in files" :key="file.title">
    <v-list-item-avatar>
      <v-icon :class="file.color" dark v-text="file.icon"></v-icon>
    </v-list-item-avatar>

    <v-list-item-content>
      <v-list-item-title v-text="file.title"></v-list-item-title>

      <v-list-item-subtitle v-text="file.subtitle"></v-list-item-subtitle>
    </v-list-item-content>

    <v-list-item-action>
      <v-btn icon>
        <v-icon color="grey lighten-1">mdi-information</v-icon>
      </v-btn>
    </v-list-item-action>
  </v-list-item>
</v-list>
```

```js
data: () => ({
    files: [
        {
            color: 'blue',
            icon: 'mdi-clipboard-text',
            subtitle: 'Jan 20, 2014',
            title: 'Vacation itinerary',
        },
        {
            color: 'amber',
            icon: 'mdi-gesture-tap-button',
            subtitle: 'Jan 10, 2014',
            title: 'Kitchen remodel',
        },
    ],
    folders: [
        {
            subtitle: 'Jan 9, 2014',
            title: 'Photos',
        },
        {
            subtitle: 'Jan 17, 2014',
            title: 'Recipes',
        },
        {
            subtitle: 'Jan 28, 2014',
            title: 'Work',
        },
    ],
}),
```
