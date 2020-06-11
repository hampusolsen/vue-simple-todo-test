<template>
  <div>
    <p v-bind:class="{'completed':item.complete}">
      <input type="checkbox" @change="markComplete" v-bind:checked="item.complete"/>
      {{item.title}}
      <button @click="$emit('delete-item', item.id)"/>
    </p>
  </div>
</template>

<script>

export default {
  name: 'Item',
  props: ['item', 'deleteItem'],
  methods: {
    markComplete () {
      this.item.complete = !this.item.complete
    }
  }
}
</script>

<style lang="scss" scoped>
  .completed {
    text-decoration: line-through;
  }

  p {
    padding: 14px 22px;
    margin: 0;
    display: flex;
    align-items: center;
    background-color: whitesmoke;
    border-bottom: 1px solid lightgray;
    &:hover {
      background-color: #fdfdfd;
    }
  }

  input[type="checkbox"] {
    margin-right: 14px;
  }

  button {
    border-radius: 50%;
    width: 36px;
    height: 36px;
    background-color: white;
    position: relative;
    display: block;
    margin-left: auto;
    &:hover {
      background-color: #eee;
    }
    &::after, &::before {
      content: "";
      position: absolute;
      top: 50%;
      left: 50%;
      width: 2px;
      height: 16px;
      background-color: #444;
    }
    &::after {
      transform: translate(-50%, -50%) rotate(45deg);
    }
    &::before {
      transform: translate(-50%, -50%) rotate(-45deg);
    }
  }

</style>
