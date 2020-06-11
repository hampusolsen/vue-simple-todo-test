<template>
  <div id="app">
    <Header />
    <AddItem @add-item="addItem" />
    <List v-bind:items="items" @delete-item="deleteItem"/>
  </div>
</template>

<script>
import { v4 as uuid } from 'uuid'

import Header from './components/Header.vue'
import AddItem from './components/AddItem.vue'
import List from './components/List.vue'

export default {
  name: 'App',
  components: {
    Header,
    AddItem,
    List
  },
  methods: {
    addItem (item) {
      this.items = [...this.items, item]
    },
    deleteItem (id) {
      this.items = this.items.filter(item => item.id !== id)
    }
  },
  data () {
    return {
      items: [
        {
          id: uuid(),
          title: 'Todo One',
          complete: false
        },
        {
          id: uuid(),
          title: 'Todo Two',
          complete: false
        },
        {
          id: uuid(),
          title: 'Todo Three',
          complete: true
        }
      ]
    }
  }
}
</script>

<style>
body {
  margin: 0;
  padding: 0;
  font-family: Arial, Helvetica, sans-serif;
}
</style>
