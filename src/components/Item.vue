<template>
  <div class="item-row">
    <span class="item-name">{{ item.name | capitalize }} ({{ item.qty }})</span>
    <div class="item-buttons">
    <button type="button" name="button" @click="decrementItem">-</button>
    <button type="button" name="button" @click="incrementItem">+</button>
    <button @click="removeItem">X</button>
  </div>
  </div>
</template>

<script>
export default {
  name: 'hello',
  props: {
    item: Object
  },
  computed: {
    localItem () {
      return this.item
    }
  },
  data () {
    return {
      msg: 'Welcome'
    }
  },
  methods: {
    incrementItem () {
      this.localItem.qty++
    },
    decrementItem () {
      this.localItem.qty--
      if (this.localItem.qty <= 0) {
        this.removeItem()
      }
    },
    removeItem () {
      this.$emit('remove', this.localItem)
    }
  },
  filters: {
    capitalize: function (value) {
      if (!value) return ''
      value = value.toString()
      return value.charAt(0).toUpperCase() + value.slice(1)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.item-row {
  min-width: 80%;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  padding-top: 5px;
}
.item-name {
  font-size: 20px;
}

button {
  background-color: white;
  border: 1px dashed;
  border-color: lightblue;
  border-radius: 8px;
  width: 3em;
  height: 3em;
  outline: none;
  margin: 0 8px 0 8px;
}
button:hover {
  background-color: lightblue;
}
</style>
