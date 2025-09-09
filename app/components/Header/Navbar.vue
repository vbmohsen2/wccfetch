<template>
  <div class="relative  ">
    <transition name="slide-fade">
      <div v-if="showNavbar"   class="w-full flex justify-center border-none absolute py-2  gap-4 mx-auto overflow-auto
               bg-white dark:bg-neutral-900 "
                     >

        <span
            v-for="cat in categories.slice(0, 8)"
            :key="cat.id"
            class="cursor-pointer font-light hover:bg-gray-500  p-2 rounded-2xl text-nowrap "
        >
          {{ cat.name }}
        </span>
      </div>
    </transition>

    <div
        class="w-full  absolute flex justify-center border-none gap-3
        bg-white dark:bg-neutral-900/90
        overflow-auto  transition-all duration-300 ease-in-out"
        :class="{ 'top-0': !showNavbar, 'top-10': showNavbar }"
    >
           <span class="pt-4"><svg xmlns="http://www.w3.org/2000/svg"
       shape-rendering="geometricPrecision"
       text-rendering="geometricPrecision"
       image-rendering="optimizeQuality"
       fill-rule="evenodd"
       clip-rule="evenodd"
       viewBox="0 0 384 511.4"
       width="24" height="24">
    <defs>
      <linearGradient id="a" gradientUnits="userSpaceOnUse" x1="163.52" y1="286.47" x2="163.52" y2="500.71">
        <stop offset="0" stop-color="#FB6404"/>
        <stop offset="1" stop-color="#F2BE10"/>
      </linearGradient>
    </defs>
    <path fill="#E20919"
          d="M77.46 228.43C65.33 119.85 128.78 43.48 247.72 0c-72.85 94.5 62.09 196.88 69.53 295.03 17.44-29.75 27.34-69.48 29.3-122.55 89.18 139.92 15.25 368.59-181.02 335.73-18.02-3.01-35.38-8.7-51.21-17.17C42.76 452.8 0 369.53 0 290c0-50.69 21.68-95.95 49.74-131.91 3.75 35.23 11.73 61.51 27.72 70.34z"/>
    <path fill="url(#a)"
          d="M139.16 372.49c-21.83-57.66-18.81-150.75 42.33-183.41.43 107.03 103.57 120.64 84.44 234.9 17.64-20.39 26.51-53.02 28.1-78.75 27.96 65.38 6.04 117.72-33.81 144.37-121.15 81-225.48-83.23-156.11-173.26 2.08 20.07 26.14 51.12 35.05 56.15z"/>
  </svg>
</span>
      <span
          v-for="cat in trendingCategories"
          :key="cat.id"
          class="  font-light cursor-pointer border border-black dark:border-gray-600 hover:bg-gray-600 p-2 my-2 rounded-2xl text-nowrap transition"
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