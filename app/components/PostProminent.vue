<template>
  <div class=" text-white rounded-lg shadow-lg overflow-hidden">
    <div
      class="relative w-full h-80 bg-cover bg-center"
      :style="{ backgroundImage: `url(${post.image})` }"
    >
      <div class="hidden lg:block absolute bottom-0 left-0 p-6  from-gray-900 via-gray-900/50 to-transparent w-full">
        <h2 class="box-decoration-clone  text-xl/loose font-bold bg-gradient-to-l from-rose-500 to-orange-400 p-1">{{ post.title }}</h2>
        <div class="flex items-center text-sm text-gray-400 mt-2">
          <span>{{ post.author }}</span>
          <span class="mx-2">•</span>
          <span>{{ post.comments }} کامنت</span>
          <span class="mx-2">•</span>
          <span>{{ post.age }}</span>
        </div>
      </div>
    </div>

    <div class="p-6 lg:hidden ">
      <h2 class="text-3xl font-bold mb-2">{{ post.title }}</h2>
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
      title: 'عنوان پست',
      author: 'نام نویسنده',
      image: 'https://via.placeholder.com/1920x1080',
      comments: 12,
      age: '2 روز پیش'
    })
  }
});
</script>