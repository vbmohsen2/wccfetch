<template>
  <transition name="slide-fade">
    <div

        class="fixed top- py-2 inset-x-0 z-40

             text-black dark:text-white shadow-md"
    >
      <div class="max-w-7xl mx-auto flex justify-center gap-2 py-2 overflow-auto ">
        <span
            v-for="cat in categories.slice(0,8)"
            :key="cat.id"
            class="cursor-pointer hover:bg-gray-500 p-2 rounded-2xl text-nowrap transition"
        >
          {{ cat.name }}
        </span>
      </div>
    </div>
  </transition>
</template>

<script setup>
import {onBeforeUnmount, onMounted, ref} from "vue"

const showBanner = ref(true)


const handleScroll = () => {
  showBanner.value = window.scrollY < 20 // کمتر از 20px بنر دیده بشه
}

onMounted(() => window.addEventListener("scroll", handleScroll))
onBeforeUnmount(() => window.removeEventListener("scroll", handleScroll))
// دسته‌بندی‌ها بدون زیر دسته
const categories = ref([
  { id: 1, name: "جنگ" },
  { id: 2, name: "۱۲ روزه" },
  { id: 3, name: "هوش مصنوعی" },
  { id: 4, name: "فرهنگ و هنر" },
  { id: 5, name: "علم و فناوری" },
  { id: 6, name: "سلامت" },
  { id: 7, name: "محیط زیست" }
])
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
.slide-fade-enter-to,
.slide-fade-leave-from {
  opacity: 1;
  transform: translateY(0);
}
</style>
