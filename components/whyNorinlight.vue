<template>
  <div class="container mt-[102px]">
    <div class="flex justify-between mb-10 items-center">
      <h4 class="font-bold text-[40px]">Почему NORNLIGHT?</h4>
      <button
        class="flex items-center py-[8px] gap-[10px] w-[220px] rounded-full border border-primary"
      >
        <p class="ml-12 font-medium text-primary">О компании</p>
        <p class="text-3xl font-medium text-primary">&rarr;</p>
      </button>
    </div>
    <div class="grid grid-cols-4 gap-5">
      <div
        class="p-10 pb-[47px] w-full h-full border border-[#D9D9D9] flex gap-[79px] flex-col-reverse justify-end"
        v-for="(item, index) in images"
        :key="index"
      >
        <div class="flex flex-col w-full items-center ">
          <p class="text-primary font-medium text-lg">
            {{ datas[index].title }}
          </p>
          <p class="text-primary mt-5 font-medium text-sm group cursor-pointer">
            {{ datas[index].price }}
          </p>
        </div>
        <img class="w-1/3" :src="item" alt="" />
      </div>
    </div>
  </div>
</template>

<script setup>
const images = ref(["/nor1.png", "/img2.jpg", "/nor1.png", "/img4.png"]);

const datas = ref([
  {
    title: "Только проверенные бренды",
    price: "Бренды, проверенные временем и качеством",
  },
  {
    title: "Самые низкие цены",
    price: "Ниже не будет нигде",
  },
  {
    title: "Быстрая доствка",
    price: "Доставляем по всей РФза 1-10 дней",
  },
  {
    title: "Большой ассортимент",
    price: "Более 1000 товаров",
  },
]);
</script>
