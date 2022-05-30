# Computed Properties:-

## ways to display data in the UI

- static HTML
- text interpolation
- Simple Expression
- Methods
- computed properties


:- Properties that can be bound to the template like data properties.

:- They are used for composing new data from existing sources.

:- They are highly performant as they are cached calculations which only update when their dependencies change.

# Computed Properties vs Methods:-

<template>
  <h2>Method Total - {{getTotal()}}</h2>
  <input type="text" v-model="country">
</template>

export default {
  name: "App",
  data() {
    return {
     country: ''
    }
  }


  methods: {
    getTotal()
    {
      console.log('getTotal Methods')
      return this.items.reduce((total, curr) => (total = total +          curr.price),0);
    }
  },
};
