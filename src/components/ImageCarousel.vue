<script setup>
import {ref, onMounted, nextTick} from "vue";
const items = ref([
  'https://plus.unsplash.com/premium_photo-1684407617236-c60dc693293a?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8MXx8cHJvZHVjdHxlbnwwfDB8MHx8fDA%3D&auto=format&fit=crop&w=500&q=60',
  'https://images.unsplash.com/photo-1559056199-641a0ac8b55e?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8OXx8cHJvZHVjdHxlbnwwfDB8MHx8fDA%3D&auto=format&fit=crop&w=500&q=60',
  'https://images.unsplash.com/photo-1527864550417-7fd91fc51a46?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8MTh8fHByb2R1Y3R8ZW58MHwwfDB8fHww&auto=format&fit=crop&w=500&q=60',
  'https://plus.unsplash.com/premium_photo-1679913792906-13ccc5c84d44?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8MjV8fHByb2R1Y3R8ZW58MHwwfDB8fHww&auto=format&fit=crop&w=500&q=60',
  'https://images.unsplash.com/photo-1520931061294-db3e762a9273?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8Mjh8fHByb2R1Y3R8ZW58MHwwfDB8fHww&auto=format&fit=crop&w=500&q=60',
  'https://images.unsplash.com/photo-1622480914645-8fa9b36178a5?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8NDB8fHByb2R1Y3R8ZW58MHwwfDB8fHww&auto=format&fit=crop&w=500&q=60',
])
let carousel =null
const newItem = ref('https://plus.unsplash.com/premium_photo-1670537995391-c8dc4da967ad?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8NDl8fHByb2R1Y3R8ZW58MHwwfDB8fHww&auto=format&fit=crop&w=500&q=60')
onMounted(()=>{
  carousel = new Flickity('#carousel')
})
function addNewItem(){
  items.value.push(newItem.value)
  carousel.destroy()
  nextTick(function (){
    carousel = new Flickity('#carousel',{})
  })
}

</script>

<template>
  <div class="my-10 flex justify-center">
    <input type="text" class="border" v-model="newItem">
    <button @click="addNewItem()" class="ml-2 bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">
      Button
    </button>
  </div>
  <div class="my-10">
    <div class="mx-auto items bg-white rounded-lg" id="carousel">
      <div :style="`background-image:url(${item})`" class="item rounded-md px-6 py-3" v-for="(item, index) in items" :key="item">{{ index + 1 }} / {{ items.length }}</div>
    </div>
  </div>
</template>

<style scoped>
.items {
  width: 600px;
  height: 400px;
}

.item {
  width: 600px;
  height: 400px;
  background-color: #ccc;
  background-size: cover;
}
</style>