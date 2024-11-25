<script setup>
import Cart from './Cart.vue'

defineProps({
  items: Array,
})

const onClickAdd = () => {
  alert('asf')
}
</script>

<template>
  <div class="grid grid-cols-4 gap-5">
    <Cart
      :key="item.id"
      v-for="item in items"
      :image-url="item.imageUrl"
      :title="item.title"
      :price="item.price"
      is-added="true"
      is-favorite="false"
      :onClickAdd="onClickAdd"
    />
  </div>
</template>
