# Date

**WIP: This component is still looking for more testers and some feedback.**

A date picker with accessibility baked in.

- [Source](https://github.com/AustinGil/vuetensils/blob/master/src/components/VDate/VDate.vue)

Features:
- Manages ARIA roles, labels, and attributes.
- Manages focus ring and traps focus within calendar.
- Provides keyboard navigation support (see below).
- Supports passing in min and max date props.

**Keyboard navigation:**

Key              | Action
:--              | :--
Enter/Spacebar   | Select the currently focused date and hide the calendar.
Right            | Move to next day.
Left             | Move to previous day.
Down             | Move to next week.
Up               | Move to previous week.
Home             | Move to beginning of week.
End              | Move to beginning of week.
PageUp           | Move to previous month.
Shift + PageUp   | Move to previous year.
PageDown         | Move to next month.
Shift + PageDown | Move to next year.
Esc              | Hide the calendar without selecting a date.

**NOTE:** I would probably recommend using the browser's [built in date picker](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/date) (`<input type="date">`) because it's simpler, consistent across website, and it's less code. However, it does not support custom styling.

## Installation

Globally:

```js
// main.js
import Vue from 'vue';
import { VDate } from 'vuetensils/src/components';

Vue.component('VDate', VDate);
```

Locally:

```vue
<script>
// SomeComponent.vue
import { VDate } from 'vuetensils/src/components';

export default {
  components: {
    VDate,
  },
  // ...
};
</script>
```

## Default Example

```vue live
<template>
  <VDate />
</template>
```

## v-model
```vue live
<template>
  <div>
    Selected Date: {{ date }}
    <VDate v-model="date" />
  </div>
</template>

<script>
export default {
  data: () => ({
    date: new Date(),
  }),
};
</script>
```

## Custom Toggle
```vue live
<template>
  <VDate>
    <template #default="{ bind, on }">
      <button v-bind="bind" v-on="on">
        Calendar!
      </button>
    </template>
  </VDate>
</template>
```

## Min and Max

```vue live
<template>
  <VDate date="Nov 3, 2020" min="Nov 2, 2020" max="Nov 4, 2020" />
</template>
```

## Localization

```vue live
<template>
  <VDate
    :days-of-week="daysOfWeek"
    :month-labels="monthLabels"
    :button-labels="buttonLabels"
  />
</template>

<script>
export default {
  data: () => ({
    daysOfWeek: Object.freeze({
      Dim: 'Dimanche',
      Lun: 'Lundi',
      Mar: 'Mardi',
      Mer: 'Mercredi',
      Jeu: 'Jeudi',
      Ven: 'Vendredi',
      Sam: 'Samedi',
    }),

    monthLabels: [
      'Janvier',
      'Février',
      'Mars',
      'Avril',
      'Mai',
      'Juin',
      'Juillet',
      'Août',
      'Septembre',
      'Octobre',
      'Novembre',
      'Décembre',
    ],

    buttonLabels: Object.freeze({
      selectDate: 'Sélectionner la date',
      showCalendar: 'montrer le calendrier',
      previousMonth: 'mois précédent',
      nextMonth: 'mois suivant',
      previousYear: 'année précédente',
      nextYear: 'année suivante',
    })
  }),
}
</script>
```

## Inline

```vue live
<template>
  <VDate inline />
</template>
```

<!-- ## Custom Classes

This component can accept a `classes` prop to customize the output HTML classes:

```
:classes="{ root: 'root-class', content: 'content-class' }"
``` -->
