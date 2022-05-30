<template>
  <h2>Full name - {{ firstName }} {{ lastName }}</h2>
  <h2>Computed fullName - {{ fullName }}</h2>
  <button @click="changeFullName">Change Fullname</button> <!-- Computed setter -->
  <!-- <h2>
    Total - {{ items.reduce((total, curr) => (total = total + curr.price), 0) }}
  </h2> -->
  <button @click="items.push({id:4, title:'keybourd',price: 50})">Add Item</button>
  <h2>Computed Total - {{ total }}</h2>
  <h2>Method Total - {{getTotal()}}</h2>
  <input type="text" v-model="country">

  <template v-for="item in items" :key="item.id">
    <h2 v-if="item.price > 100">{{ item.title }} {{item.price}}</h2>
  </template>
</template>

<h2 v-for='item in expensiveItems' :key='item.id'>
    {{ item.title }} {{ item.price }}
</h2>

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
      country: ''
    }
  },
  methods: {
    getTotal(){
      console.log('getTotal Methods')
      return this.items.reduce((total, curr) => (total = total + curr.price),0)
    },
    changeFullName(){   //computed setter
      this.fullName = 'clark kent'
    }
  },
  computed: {
    // fullName() {
    //   return `${this.firstName} ${this.lastName}`
    // },
     fullName: {    //computed setter
       get(){
         return `${this.firstName} ${this.lastName}`
       },
      set(value){
        const names = value.split(' ')
        this.firstName = names[0],
        this.lastName = names[1]
      }
    },
    total() {
      console.log("total computed properties")
      return this.items.reduce((total, curr) => (total = total + curr.price),0)
    },
    expensiveItems(){ 
      return this.items.filter( item => item.price > 100)
    }
  },
}
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
