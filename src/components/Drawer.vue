<script setup>
import DrawerHead from './Drawer-head.vue'
import BasketListItem from './BasketListItem.vue'
</script>

<template>
  <div class="fixed top-0 left-0 h-full w-full bg-black z-10 opacity-70"></div>
  <div class="bg-white w-96 h-full fixed right-0 top-0 z-20 p-8">
    <Drawer-head />
    <BasketListItem />

    <div class="flex flex-col gap-5 mb-6 mt-7">
      <div class="flex gap-2">
        <span>Итого:</span>
        <div class="flex-1 border-b border-dashed"></div>
        <b>12900 rub.</b>
      </div>
      <div class="flex gap-2">
        <span>Налог 5%:</span>
        <div class="flex-1 border-b border-dashed"></div>
        <b>900 rub.</b>
      </div>
      <button
        class="bg-lime-500 w-full rounded-xl py-3 text-white mt-4 disabled:bg-slate-300 hover:bg-lime-600 transition active:bg-lime-700 cursor-pointer"
      >
        Оформить заказ
      </button>
    </div>
  </div>
</template>
