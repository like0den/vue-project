<script setup>
import { ref } from "vue";

const header = ref("Shopping List App");
const items = ref([
  { id: 1, label: "10 party hats" },
  { id: 2, label: "2 boards games" },
  { id: 3, label: "20 cups" },
]);
const newItem = ref("");
const newItemPriority = ref("low");
const newItemSelectBox = ref("low");
const newItemCheckBox = ref(false);
const iceCreamFlavors = ref([]);
</script>

<template>
  <h1>{{ header }}</h1>
  <form
    class="add-item-form"
    @submit.prevent="items.push({ id: items.length + 1, label: newItem })"
  >
    <input v-model.trim="newItem" type="text" placeholder="Add an item" />
    <!-- ラジオボタン -->
    Priority:
    <label>
      <input type="radio" v-model="newItemPriority" value="low" />
      Low
    </label>
    <label>
      <input type="radio" v-model="newItemPriority" value="high" />
      High
    </label>
    <br />
    <!-- セレクトボックス -->
    <label>
      Priority:
      <select v-model="newItemSelectBox">
        <option value="low">Low</option>
        <option value="high">High</option>
      </select>
    </label>
    <br />
    <!-- チェックボックス -->
    <label>
      <input type="checkbox" v-model="newItemCheckBox" />
      High Priority
      {{ newItemCheckBox }}
    </label>
    <br />
    <!-- リスト -->
    <label>
      <input type="checkbox" v-model="iceCreamFlavors" value="vanilla" />Vanilla
    </label>
    <label>
      <input
        type="checkbox"
        v-model="iceCreamFlavors"
        value="Chocolate"
      />Chocolate
    </label>
    <label>
      <input
        type="checkbox"
        v-model="iceCreamFlavors"
        value="strawberry"
      />Strawberry
    </label>
    <br />
    <!-- ボタン -->
    <button class="btn btn-primary">Save Item</button>
    <!-- リスト -->
    <ul>
      <li v-for="{ id, label } in items" :key="id">
        {{ label }}
      </li>
    </ul>
  </form>
</template>
