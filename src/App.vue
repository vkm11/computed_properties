<template>
  <h2>Full name - {{ firstName }} {{ lastName }}</h2>
  <h2>Computed fullName - {{ fullName }}</h2>
  <!-- <h2>
    Total - {{ items.reduce((total, curr) => (total = total + curr.price), 0) }}
  </h2> -->
  <button @click="items.push({id:4, title:'keybourd',price: 50})">Add Item</button>
  <h2>Computed Total - {{ total }}</h2>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      firstName: "Bruce",
      lastName: "wayne",
      items: [
        {
          id: 1,
          title: "TV",
          price: 100,
        },
        {
          id: 2,
          title: "Phone",
          price: 200,
        },
        {
          id: 3,
          title: "Laptop",
          price: 300,
        },
      ],
    };
  },
  methods: {},
  computed: {
    fullName() {
      return `${this.firstName} ${this.lastName}`;
    },
    total() {
      return this.items.reduce(
        (total, curr) => (total = total + curr.price),
        0
      );
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
