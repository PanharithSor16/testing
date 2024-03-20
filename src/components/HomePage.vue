<script setup>
import { ref } from "vue";

const listItem = ref(["apple", "lsome"]);
const newItemText = "";
function adding() {
  console.log("clicked");
  console.log(listItem);
  if (this.newItemText.trim() !== "") {
    this.listItem.push(this.newItemText.trim());
    this.newItemText = ""; // Clear input field after adding item
  }
}

function deleteItem(index) {
  this.listItem.splice(index, 1);
}
</script>
<template>
  <section class="w-full m-8 items-center">
    <div class="ml-10 w-3/4 items-center">
      <h1
        class="bg-slate-600 shadow-lg h-10 shadow-blue-500/50 text-red-50 text-center text-lg font-semibold uppercase border-gray-300 rounded"
      >
        ToDo
      </h1>
      <div class="space-x-8 mt-8">
        <input
          type="text"
          v-model="newItemText"
          class="border w-2/3 shadow-lg shadow-blue-500/50 border-gray-300 bg-white h-10 px-4 rounded-md text-sm focus:outline-none focus:border-blue-500"
          placeholder="Enter text..."
        />
        <button
          class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 shadow-lg shadow-blue-500/50 px-4 rounded text-center"
          @click="adding()"
        >
          ADD+
        </button>
      </div>
    </div>
    <div
      class="mt-10 ml-10 bg-slate-100 text-blue-300 text-center items-end w-1/2 font-bold"
    >
      <ul class="list-none mt-1 space-y-1 items-end">
        <li
          v-for="(item, index) in listItem"
          :key="index"
          class="border-gray-500 h-10 bg-red-400 place-items-end rounded-md self-center"
        >
          {{ item }}
          <button
            class="flex-col items-end ml-20 bg-slate-600 text-white font-bold py-2 shadow-lg shadow-blue-500/50 px-4 rounded text-center"
            @click="deleteItem(index)"
          >
            Delete
          </button>
        </li>
      </ul>
    </div>
  </section>
</template>
