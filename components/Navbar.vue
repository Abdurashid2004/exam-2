<template>
  <div class="container pt-5">
    <div
      class="max-md:hidden flex w-full justify-between mb-2 text-primary font-semibold text-sm"
    >
      <div class="flex gap-7">
        <nuxt-link
          v-for="(item, index) in sections"
          :key="index"
          :to="item.path"
          class="opacity-50"
        >
          {{ item.name }}
        </nuxt-link>
      </div>
      <div class="flex gap-6">
        <p class="opacity-100">8 (800) 890-46-56</p>
        <a href="#" class="opacity-50">Заказать звонок</a>
      </div>
    </div>
  </div>
  <div
    class="sticky top-0 left-0 w-full py-3 z-30"
    :class="isScrolled ? 'backdrop-blur-lg bg-gradient-to-r' : 'bg-white'"
  >
    <div class="container">
      <div class="flex w-full items-center justify-between gap-4">
        <div class="flex gap-[29px]">
          <a href="/"><img src="/MainLogo.svg" class="cursor-pointer" alt="Logo" /></a>
          <button
            @click="dropdownClick = !dropdownClick"
            class="flex px-[27px] gap-[9px] cursor-pointer items-center rounded-full bg-primary py-[14px]"
          >
            <img src="/catalog.svg" alt="category" />
            <p class="text-white font-semibold">Каталог</p>
          </button>
        </div>
        <div class="relative w-[45%]">
          <input
            class="font-semibold bg-white/50 outline-none pl-[27px] pr-12 h-full py-[14px] placeholder:text-primary border border-primary rounded-full w-full"
            type="text"
            placeholder="Поиск по товарам"
          />
          <img
            class="absolute top-1/2 -translate-y-1/2 right-0 -translate-x-3/4 z-10"
            src="/search.svg"
            alt="search"
          />
        </div>
        <div
          class="flex h-full items-center"
          v-for="(item, index) in image"
          :key="index"
        >
          <div class="flex flex-col items-center gap-[6px]">
            <img
              :src="item"
              class="cursor-pointer"
              :class="index + 1 != image.length ? 'w-1/3' : 'w-1/2'"
              alt="Logos "
            />
            <p class="text-[12px] font-semibold text-primary">
              {{ bottomSections[index] }}
            </p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from "vue";

const dropdownClick = ref(false);

const sections = ref([
  { name: "О компании", path: '/About-us' },
  { name: "Доставка и оплата", path: '/deliver' },
  { name: "Возврат", path: '/return' },
  { name: "Гарантии", path: '/garant' },
  { name: "Контакты", path: '/contacts' },
  { name: "Блог", path: '/blog' },
]);

const bottomSections = ref(["Избранное", "Сравнение", "Корзина"]);
const image = ref(["/like5.svg", "/compare.svg", "/cart.svg"]);

const isScrolled = ref(false);

const handleScroll = () => {
  isScrolled.value = window.scrollY > 0;
};

onMounted(() => {
  window.addEventListener("scroll", handleScroll);
});

onUnmounted(() => {
  window.removeEventListener("scroll", handleScroll);
});
</script>

<style scoped>
.opacity-50 {
  opacity: 0.5;
}
</style>
