<template>
  <div class="relative">
    <transition name="slide-fade">
      <div v-if="showNavbar" class=" w-full flex justify-center absolute py-2 my-2 gap-4 mx-auto overflow-auto">

        <span
            v-for="cat in categories.slice(0, 8)"
            :key="cat.id"
            class="cursor-pointer hover:bg-gray-500 p-2 rounded-2xl text-nowrap transition"
        >
          {{ cat.name }}
        </span>
      </div>
    </transition>

    <div
        class="w-full absolute flex justify-center bg-inherit py-2  gap-3 overflow-auto transition-all duration-300 ease-in-out"
        :class="{ 'top-0': !showNavbar, 'top-16': showNavbar }"
    >
           <span class=""><svg xmlns="http://www.w3.org/2000/svg"
                      viewBox="0 0 24 24"
                      width="24" height="24"
                      role="img" aria-label="Hot tag">
  <title>Hot</title>
  <defs>
    <linearGradient id="flameTag" x1="0" x2="1" y1="0" y2="1">
      <stop offset="0%" stop-color="#ff5722"/>
      <stop offset="100%" stop-color="#ffc107"/>
    </linearGradient>
  </defs>
  <path
      d="M12 2C10 6 6 8 6 13c0 4 3 7 6 9 3-2 6-5 6-9 0-5-4-7-6-11z"
      fill="url(#flameTag)"
  />
</svg>
</span>
      <span
          v-for="cat in trendingCategories"
          :key="cat.id"
          class="cursor-pointer border border-b-gray-700 hover:bg-gray-600 p-2 my-2 rounded-2xl text-nowrap transition"
      >
        {{ cat.name }}
      </span>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount } from "vue";

const showNavbar = ref(true);

const handleScroll = () => {
  showNavbar.value = window.scrollY < 20;
};

onMounted(() => window.addEventListener("scroll", handleScroll));
onBeforeUnmount(() => window.removeEventListener("scroll", handleScroll));

const categories = ref([
  { id: 1, name: "سیاست" },
  { id: 2, name: "اقتصاد" },
  { id: 3, name: "ورزش" },
  { id: 4, name: "فرهنگ و هنر" },
  { id: 5, name: "علم و فناوری" },
  { id: 6, name: "سلامت" },
  { id: 7, name: "محیط زیست" },
  { id: 8, name: "بین‌الملل" },
]);

const trendingCategories = ref([
  { id: 1, name: "جنگ" },
  { id: 2, name: "۱۲ روزه" },
  { id: 3, name: "هوش مصنوعی" },
  { id: 4, name: "فرهنگ و هنر" },
  { id: 5, name: "علم و فناوری" },
  { id: 6, name: "سلامت" },
  { id: 7, name: "محیط زیست" },
]);
</script>

<style scoped>
.slide-fade-enter-active,
.slide-fade-leave-active {
  transition: all 0.3s ease;
}
.slide-fade-enter-from,
.slide-fade-leave-to {
  opacity: 0;
  transform: translateY(-100%);
}
</style>
---

### ۲. توضیح تغییرات
* **حذف کلاس `top-5` از کلاس ثابت:** کلاس `top-5` رو از `class="..."` حذف کردیم.
* **استفاده از کلاس پویا برای هر دو حالت:** حالا از یک `object` در `:class` استفاده می‌کنیم که دو حالت رو مدیریت می‌کنه:
* `'top-0': !showNavbar`: وقتی اسکرول می‌کنی و `showNavbar` به `false` تبدیل میشه، کلاس `top-0` فعال می‌شه.
* `'top-16': showNavbar`: وقتی در بالای صفحه هستی و `showNavbar` برابر با `true` هست، کلاس `top-16` فعال می‌شه. (شما باید مقدار `16` را بر اساس ارتفاع هدر اصلی و نوبار تنظیم کنی. ممکن است این مقدار برای شما متفاوت باشد.)

با این روش، در هر لحظه فقط یک کلاس موقعیت‌دهی (`top-0` یا `top-16`) فعال هست و تعارضی پیش نمی‌آید، و انیمیشن انتقال به درستی کار می‌کند.