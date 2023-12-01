<template>
  <div class="boodschappenlijst">
    <li v-for="item in items" :key="item">
      {{ item }}
    </li>
    <input type="text" v-model="newItem">
    <button @click=addItem>Voeg toe</button>
    <button @click="sortItems">Sorteer</button>
  </div>
</template>

<script>
export default {
  name: 'BoodschappenLijst',
  data() {
    return {
      items: [],
      newItem: ''
    }
  },
  methods: {
    addItem() {
      const newItems = this.newItem.split(',');
      for (let item of newItems) {
        item = item.trim();
        if (item !== '') {
          this.items.push(item);
        }
      }
      this.newItem = '';
    },
    sortItems() {
      this.items.sort();
    }
  }
}

</script>