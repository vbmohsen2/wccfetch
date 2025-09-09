<template>
  <div class=" dark:text-white rounded-lg    shadow-lg overflow-hidden">
    <div
      class="relative w-full h-80 bg-cover bg-center "
      :style="{ backgroundImage: `url(${post.image})` }"
    >
      <div class="hidden lg:block absolute bottom-0 left-0 p-6 from-gray-900 via-gray-900/50 to-transparent w-full">
        <h2 class="text-xl/loose font-bold p-1">
          <span class="box-decoration-clone bg-gradient-to-l from-rose-500 to-orange-400 p-1 rounded-sm">{{ post.title }}</span>
        </h2>
        <div class="flex items-center text-sm text-gray-400 dark:text-white mt-2">
          <span>{{ post.author }}</span>
          <span class="mx-2">•</span>
          <span>{{ post.comments }}</span>
          <span class="mx-2">•</span>
          <span>{{ post.age }}</span>
        </div>
      </div>
    </div>

    <div class="p-6 lg:hidden">
      <h2 class="text-3xl font-bold mb-2">
        <span class="rtl-hover-underline-bg">{{ post.title }}</span>
      </h2>
      <div class="flex items-center text-sm text-gray-400 mb-4">
        <span>{{ post.author }}</span>
        <span class="mx-2">•</span>
        <span>{{ post.comments }} کامنت</span>
        <span class="mx-2">•</span>
        <span>{{ post.age }}</span>
      </div>
    </div>
  </div>
</template>

<script setup>
import { defineProps } from 'vue';

const props = defineProps({
  post: {
    type: Object,
    required: true,
    default: () => ({
      title: 'عنوان پست با چند سطر متن برای آزمایش.',
      author: 'نام نویسنده',
      image: 'https://via.placeholder.com/1920x1080',
      comments: 12,
      age: '2 روز پیش'
    })
  }
});
</script>

<style scoped>
/* CSS برای انیمیشن خط زیرین با پس‌زمینه */
.rtl-hover-underline-bg {
  /* `display: inline` باعث می‌شود زیر هر سطر جداگانه خط کشیده شود */
  display: inline;
  background-image: linear-gradient(currentColor, currentColor);
  background-position: right bottom;
  background-size: 0% 2px;
  background-repeat: no-repeat;
  transition: background-size 0.5s ease-in-out;
  padding-bottom: 2px;
}

.rtl-hover-underline-bg:hover {
  background-size: 100% 2px;
}
</style>