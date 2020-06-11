<template>
  <div >
    <Item v-for="item in items" :key="item.id" v-bind:item="item" @delete-item="$emit('delete-item', item.id)" />
  </div>
</template>

<script>
import Item from './Item'

export default {
  name: 'List',
  props: ['items'],
  components: { Item }
}
</script>

<style scoped>

</style>
