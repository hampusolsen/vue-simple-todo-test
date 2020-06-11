<template>
    <div>
        <form @submit="addItem">
            <input type="text" name="title" placeholder="Item title..." v-model="title"/>
            <button type="submit">SUBMIT</button>
        </form>
    </div>
</template>

<script>
import { v4 as uuid } from 'uuid'

export default {
  name: 'AddItem',
  props: ['add-item'],
  data () {
    return {
      title: ''
    }
  },
  methods: {
    addItem (e) {
      e.preventDefault()

      const itemToAdd = {
        id: uuid(),
        complete: false,
        title: this.title
      }

      this.$emit('add-item', itemToAdd)
      this.title = ''
    }
  }
}
</script>

<style lang="scss" scoped>
form {
    display: flex;
}

input[type="text"] {
    flex: 10;
    border: 1px solid #222;
    padding-left: 12px;
}

button {
    flex: 1;
    height: 36px;
    border: 0;
    background-color: #556;
    color: white;
    &:hover {
        background-color: #557;
    }
}
</style>
