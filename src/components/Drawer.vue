<script setup>
import DrawerHead from "./DrawerHead.vue";
import CartItemList from "./CartItemList.vue";
</script>

<template>
  <div class="fixed top-0 left-0 h-full w-full bg-black z-10 opacity-70"></div>
  <div class="bg-white w-96 h-full fixed top-0 right-0 z-20 p-8">
    <DrawerHead />
    <CartItemList />

    <div class="flex flex-col gap-4 mt-7">
      <div class="flex gap-2">
        <span>Итого </span>
        <div class="flex-1 border-b border-dashed"></div>
        <b>12 990р</b>
      </div>

      <div class="flex gap-2">
        <span>Налог 5% </span>
        <div class="flex-1 border-b border-dashed"></div>
        <b>990р</b>
      </div>

      <button
        class="mt-4 bg-lime-500 w-full rounded-xl py-3 disabled:bg-slate-400 text-white cursor-pointer hover:bg-lime-600 transition active:bg-lime-700"
      >
        Оформить заказ
      </button>
    </div>
  </div>
</template>
