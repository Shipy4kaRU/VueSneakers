<script setup>
defineProps({
  title: String,
  imageUrl: String,
  price: Number,
  isFavorite: Boolean,
  isAdded: Boolean,
  onClickAdd: Function,
  onClickFavorite: Function,
});
</script>

<template>
  <div
    class="relative p-8 bg-white border border-slate-100 rounded-2xl cursor-pointer hover:translate-y-2 hover:shadow-xl transition"
  >
    <div>
      <img
        :src="!isFavorite ? '/like-1.svg' : '/like-2.svg'"
        alt="Like"
        class="absolute top-8 left-8"
        @click="onClickFavorite"
      />
      <img :src="imageUrl" alt="Sneaker" />
      <p class="mt-5">{{ title }}</p>

      <div class="flex justify-between mt-5">
        <div class="flex flex-col">
          <span class="text-slate-400">Цена: </span>
          <b>{{ price }} руб.</b>
        </div>
        <button @click="onClickAdd">
          <img :src="!isAdded ? '/plus.svg' : '/checked.svg'" alt="Add" />
        </button>
      </div>
    </div>
  </div>
</template>
