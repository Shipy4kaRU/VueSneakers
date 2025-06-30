<script setup lang="ts">
import Header from "./components/Header.vue";
import CardList from "./components/CardList.vue";
import { onMounted, ref, reactive, watch } from "vue";
import axios from "axios";
// import Drawer from "./components/Drawer.vue";

const items = ref([]);

const filters = reactive({
  sortBy: "title",
  searchQuery: "",
});

const onChangeSearchInput = (e) => {
  filters.searchQuery = e.target.value;
};

const onChangeSelect = (e) => {
  filters.sortBy = e.target.value;
};

const getItems = () => {
  const params: Record<string, string> = {
    sortBy: filters.sortBy,
  };

  if (filters.searchQuery) params.title = `*${filters.searchQuery}*`;

  axios
    .get("https://604781a0efa572c1.mokky.dev/items", {
      params,
    })
    .then(
      (res) => (items.value = res.data),
      (err) => console.log(err)
    );
};

onMounted(() => {
  getItems();
});

watch(filters, () => {
  getItems();
});
</script>

<template>
  <div class="w-4/5 m-auto bg-white rounded-xl shadow-xl mt-14">
    <Header />

    <div class="p-10">
      <div class="flex justify-between items-center">
        <h2 class="text-3xl font-bold mb-8">Все кроссовки</h2>

        <div class="flex gap-4">
          <select
            @change="onChangeSelect"
            class="py-2 px-3 border rounded-md outline-none"
          >
            <option value="name">По названию</option>
            <option value="price">По цене (дешевые)</option>
            <option value="-price">По цене (дорогие)</option>
          </select>

          <div class="relative">
            <img
              src="/search.svg"
              alt="Search"
              class="absolute left-4 top-2.5"
            />
            <input
              @input="onChangeSearchInput"
              type="text"
              placeholder="Поиск..."
              class="border rounded-md py-1.5 pl-11 pr-4 outline-none focus:border-gray-400 border-gray-200 transition"
            />
          </div>
        </div>
      </div>
      <CardList :items="items" />
    </div>
  </div>
</template>

<style scoped></style>
