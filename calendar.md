# Calendars Overview

The `v-calendar` component is wrapped within a `v-sheet` component, which are containers for many components such as `v-toolbar` and `v-card`.

There are two main sections within the template:

1. `v-sheet` that holds the top `v-toolbar`
2. `v-sheet` that houses the main `v-calendar`

Then within the script there are quite a few properties to unpack, which we will come onto further down.

Here is an image of the example used:

![Screenshot from 2021-11-02 07-38-44](https://user-images.githubusercontent.com/73107656/139805057-6b5d7e09-64f1-44e2-8d94-64979af63f6c.png)

Section 1, the top `v-sheet` that houses the `v-toolbar`. This section allows the user to scroll through and view month by month, there is a quick button to go directly to focusing on today and the view can be altered to show, month, week, 4 days or day:

```html
<v-row class="fill-height">
  <v-col>
    <v-sheet height="64">
      <v-toolbar flat>
        <v-btn outlined class="mr-4" color="grey darken-2" @click="setToday">
          Today
        </v-btn>
        <v-btn fab text small color="grey darken-2" @click="prev">
          <v-icon small> mdi-chevron-left </v-icon>
        </v-btn>
        <v-btn fab text small color="grey darken-2" @click="next">
          <v-icon small> mdi-chevron-right </v-icon>
        </v-btn>
        <v-toolbar-title v-if="$refs.calendar">
          {{ $refs.calendar.title }}
        </v-toolbar-title>
        <v-spacer></v-spacer>
        <v-menu bottom right>
          <template v-slot:activator="{ on, attrs }">
            <v-btn outlined color="grey darken-2" v-bind="attrs" v-on="on">
              <span>{{ typeToLabel[type] }}</span>
              <v-icon right> mdi-menu-down </v-icon>
            </v-btn>
          </template>
          <v-list>
            <v-list-item @click="type = 'day'">
              <v-list-item-title>Day</v-list-item-title>
            </v-list-item>
            <v-list-item @click="type = 'week'">
              <v-list-item-title>Week</v-list-item-title>
            </v-list-item>
            <v-list-item @click="type = 'month'">
              <v-list-item-title>Month</v-list-item-title>
            </v-list-item>
            <v-list-item @click="type = '4day'">
              <v-list-item-title>4 days</v-list-item-title>
            </v-list-item>
          </v-list>
        </v-menu>
      </v-toolbar>
    </v-sheet>
    <v-sheet height="600">
      <v-calendar
        ref="calendar"
        v-model="focus"
        color="primary"
        :events="events"
        :event-color="getEventColor"
        :type="type"
        @click:event="showEvent"
        @click:more="viewDay"
        @click:date="viewDay"
        @change="updateRange"
      ></v-calendar>
      <v-menu
        v-model="selectedOpen"
        :close-on-content-click="false"
        :activator="selectedElement"
        offset-x
      >
        <v-card color="grey lighten-4" min-width="350px" flat>
          <v-toolbar :color="selectedEvent.color" dark>
            <v-btn icon>
              <v-icon>mdi-pencil</v-icon>
            </v-btn>
            <v-toolbar-title v-html="selectedEvent.name"></v-toolbar-title>
            <v-spacer></v-spacer>
            <v-btn icon>
              <v-icon>mdi-heart</v-icon>
            </v-btn>
            <v-btn icon>
              <v-icon>mdi-dots-vertical</v-icon>
            </v-btn>
          </v-toolbar>
          <v-card-text>
            <span v-html="selectedEvent.details"></span>
          </v-card-text>
          <v-card-actions>
            <v-btn text color="secondary" @click="selectedOpen = false">
              Cancel
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-menu>
    </v-sheet>
    <!-- Main v-sheet for v-calendar goes heres -->
  </v-col>
</v-row>
```

Section 2 shows the `v-sheet` that contains the `v-calendar`. The below example code is also split into two parts:

1. The `v-calendar` itself which has a click event that opens a pop up menu showing the specific calendar event
2. The `v-menu` which shows once an event within the calendar has been clicked on. This pop up displays the event details and is also where the user can edit the event.

```html
<v-row class="fill-height">
  <v-col>
    <!-- Top v-sheet for v-toolbar goes here -->
    <v-sheet height="600">
      <v-calendar
        ref="calendar"
        v-model="focus"
        color="primary"
        :events="events"
        :event-color="getEventColor"
        :type="type"
        @click:event="showEvent"
        @click:more="viewDay"
        @click:date="viewDay"
        @change="updateRange"
      ></v-calendar>
      <v-menu
        v-model="selectedOpen"
        :close-on-content-click="false"
        :activator="selectedElement"
        offset-x
      >
        <v-card color="grey lighten-4" min-width="350px" flat>
          <v-toolbar :color="selectedEvent.color" dark>
            <v-btn icon>
              <v-icon>mdi-pencil</v-icon>
            </v-btn>
            <v-toolbar-title v-html="selectedEvent.name"></v-toolbar-title>
            <v-spacer></v-spacer>
            <v-btn icon>
              <v-icon>mdi-heart</v-icon>
            </v-btn>
            <v-btn icon>
              <v-icon>mdi-dots-vertical</v-icon>
            </v-btn>
          </v-toolbar>
          <v-card-text>
            <span v-html="selectedEvent.details"></span>
          </v-card-text>
          <v-card-actions>
            <v-btn text color="secondary" @click="selectedOpen = false">
              Cancel
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-menu>
    </v-sheet>
  </v-col>
</v-row>
```

Lastly for the overview this calendar component comes with a decent amount of properties and functions via the `v-calendar` api. Below is the script for the example above:

```js
data: () => ({
  focus: '', // Set day to focus in on
  type: 'month', // Set the view (day, week, month etc)
  typeToLabel: {
    month: 'Month',
    week: 'Week',
    day: 'Day',
    '4day': '4 Days',
  },
  selectedEvent: {}, // showEvent passes in the event object and assigns value as the selectedEvent
  selectedElement: null, // showEvent also passes in the native event where we can grab the element (e.target)
  selectedOpen: false, // showEvent also sets selectedOpen to true
  events: [],
  colors: ['blue', 'indigo', 'deep-purple', 'cyan', 'green', 'orange', 'grey darken-1'],
  names: ['Meeting', 'Holiday', 'PTO', 'Travel', 'Event', 'Birthday', 'Conference', 'Party'],
}),
mounted () {
  this.$refs.calendar.checkChange()
},
methods: {
  // Click on a date to view that day
  viewDay ({ date }) {
    this.focus = date
    this.type = 'day'
  },
  getEventColor (event) {
    return event.color
  },
  setToday () {
    this.focus = ''
  },
  prev () {
    this.$refs.calendar.prev()
  },
  next () {
    this.$refs.calendar.next()
  },
  // Click on an event to open the dialog event pop up box
  showEvent ({ nativeEvent, event }) {
    const open = () => {
      this.selectedEvent = event
      this.selectedElement = nativeEvent.target
      requestAnimationFrame(() => requestAnimationFrame(() => this.selectedOpen = true))
    }

    if (this.selectedOpen) {
      this.selectedOpen = false
      requestAnimationFrame(() => requestAnimationFrame(() => open()))
    } else {
      open()
    }

    nativeEvent.stopPropagation()
  },
  updateRange ({ start, end }) {
    const events = []

    const min = new Date(`${start.date}T00:00:00`)
    const max = new Date(`${end.date}T23:59:59`)
    const days = (max.getTime() - min.getTime()) / 86400000
    const eventCount = this.rnd(days, days + 20)

    for (let i = 0; i < eventCount; i++) {
      const allDay = this.rnd(0, 3) === 0
      const firstTimestamp = this.rnd(min.getTime(), max.getTime())
      const first = new Date(firstTimestamp - (firstTimestamp % 900000))
      const secondTimestamp = this.rnd(2, allDay ? 288 : 8) * 900000
      const second = new Date(first.getTime() + secondTimestamp)

      events.push({
        name: this.names[this.rnd(0, this.names.length - 1)],
        start: first,
        end: second,
        color: this.colors[this.rnd(0, this.colors.length - 1)],
        timed: !allDay,
      })
    }

    this.events = events
  },
  rnd (a, b) {
    return Math.floor((b - a + 1) * Math.random()) + a
  },
},

```

## Event Properties

Each calendar event has the following object properties:

1. Name: This is the title that is shown on the card
2. Details: This is the meat of the event only shown on the dialog box
3. Start: Date and potential time
4. Finish: Date and potential time
5. Color: This is the event color that is shown on the card and dialog header
