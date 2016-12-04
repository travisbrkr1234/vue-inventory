<template>
  <div class="inventory">
    <h1>{{ msg }}</h1>
    <span>{{  }}</span>
    <input class="new-item" type="text" v-model="itemName" v-on:keyup.enter="addNewItem" placeholder="Add an Item" autofocus>

    <div class="item">
      <item v-for="item in items" @remove="removeItem" :item="item"></item>
    </div>
  </div>
</div>
</template>

<script>
import Item from './Item.vue'
export default {
  name: 'inventory',
  components: {
    Item
  },
  data () {
    return {
      msg: 'Inventory',
      itemName: '',
      items: [
        {'id': 1, 'name': 'milk', 'qty': 1},
        {'id': 2, 'name': 'eggs', 'qty': 16},
        {'id': 3, 'name': 'cheese block', 'qty': 3}
      ]
    }
  },
  methods: {
    addNewItem () {
      if (this.itemName.length > 0 && this.items.length < 100) {
        this.items.push({'id': this.items.length + 1, 'name': this.itemName, 'qty': 1})
        this.itemName = ''
      }
    },
    removeItem (item) {
      this.items = this.items.filter((copyOfItem) => {
        return copyOfItem.id !== item.id
      })
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}

input {
  width: 80%;
  height: 35px;
  margin-bottom: 10px;
  font-size: 18px;
}

.item {
  display: flex;
  flex-direction: column;
  align-items: center;
  align-content: center;
}

</style>
