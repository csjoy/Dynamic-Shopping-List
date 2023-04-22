<script setup lang="ts">

</script>

<template>
  <div class="flex justify-center items-center">
    <div class="container">
      <div class="flex justify-between min-w-lg my-8">
        <input type="text" v-model="fruit" placeholder="Press enter to add new item" class="border-2 border-blue-950 rounded-md p-2 w-5/6" @keyup.enter="addItem()">
        <button class="px-5 py-2.5 rounded-md text-white bg-blue-950 hover:bg-blue-900 active:bg-blue-950" @click="addItem()">Add item</button>
      </div>
      <div class="border-4 border-gray-200">
        <div class="p-8">
          <div v-for="(fruit, index) in fruits" :key="index">
            <div class="flex justify-between p-4">
              <p class="text-xl text-gray-500 font-medium">{{ fruit }}</p>
              <button class="text-rose-600 font-semibold" @click="deleteItem(index)">REMOVE</button>
            </div>
          </div>
        </div>
      </div>
      <div class="flex justify-center items-center">
        <button class="rounded-md text-white text-xl font-medium bg-rose-500 px-5 py-2 5 my-8 text-center" @click="deleteAll()">Delete all</button>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
export default {
  data() {
    return {
      fruits: ["Apples", "Bananas", "Carrots"],
      fruit: ""
    }
  },
  methods: {
    addItem() {
      this.fruit = this.fruit.trim()
      if (this.fruit) {
        this.fruits.push(this.fruit)
        this.fruit = ""
      }

    },
    deleteItem(fruit: number) {
      if (fruit < 0 || fruit > this.fruits.length) return
      this.fruits = this.fruits.filter((_, index) => index !== fruit)
    },
    deleteAll() {
      this.fruits = []
    }
  }
}
</script>