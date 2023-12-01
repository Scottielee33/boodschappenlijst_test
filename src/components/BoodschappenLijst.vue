<template>
  <div class="boodschappenlijst">
    <div v-for="item in items" :key="item.name">
      <input type="checkbox" v-model="item.checked">
      {{ item.name }}
    </div>
    <input type="text" v-model="newItem">
    <button @click="addItem">Voeg toe</button>
    <button @click="sortItems">Sorteer</button>
    <button @click="deleteChecked">Verwijder geselecteerde</button>
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
      for (let name of newItems) {
        name = name.trim();
        if (name !== '') {
          this.items.push({ name, checked: false });
        }
      }
      this.newItem = '';
    },
    sortItems() {
      this.items.sort((a, b) => a.name.localeCompare(b.name));
    },
    deleteChecked() {
      this.items = this.items.filter(item => !item.checked);
    }
  }
}
</script>