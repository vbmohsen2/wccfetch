<template>
  <div class="relative p-3  rounded-xl  hover:bg-gray-500" >
    <!-- آیکون سرچ -->
    <button
        @click="toggleSearch"
        class="my-2"
        aria-label="Search"
    >
      <svg xmlns="http://www.w3.org/2000/svg"
                         viewBox="0 0 24 24"
                         width="24" height="24"
                         role="img" aria-label="Search"
                         fill="none" stroke="currentColor"
                         stroke-width="1.3" stroke-linecap="round" stroke-linejoin="round">
                      <title>search</title>
                      <!-- دایره ذره‌بین -->
                      <circle cx="11" cy="11" r="5.5" />
                      <!-- دسته ذره‌بین -->
                      <line x1="15.5" y1="15.5" x2="18" y2="19" />
                    </svg>
    </button>

    <!-- لایه پس‌زمینه -->
    <transition name="fade">
      <div v-if="isOpen"
           @click="closeSearch"
           class="fixed inset-0 bg-black/40 z-40"></div>
    </transition>

    <!-- کادر سرچ -->
    <transition name="slide-down">
      <div v-if="isOpen"
           class="fixed top-0 inset-x-0 z-50 bg-white dark:bg-gray-900 shadow-md p-4">
        <div class="max-w-2xl mx-auto flex items-center gap-2">
          <input
              type="text"
              placeholder="جستجو..."
              class="flex-1 px-4 py-2 rounded-lg border border-gray-300 dark:border-gray-700
                   bg-gray-50 dark:bg-gray-800 text-gray-900 dark:text-white
                   focus:outline-none focus:ring-2 focus:ring-blue-500"
          />
          <button @click="closeSearch"
                  class="text-gray-500 hover:text-red-500 transition">
            ✕
          </button>
        </div>
      </div>
    </transition>
  </div>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue'

const isOpen = ref(false)

const toggleSearch = () => {
  isOpen.value = !isOpen.value
}

const closeSearch = () => {
  isOpen.value = false
}

// بستن با Esc
const handleKey = (e) => {
  if (e.key === 'Escape') closeSearch()
}

onMounted(() => {
  window.addEventListener('keydown', handleKey)
})

onBeforeUnmount(() => {
  window.removeEventListener('keydown', handleKey)
})
</script>

<style scoped>
/* انیمیشن‌ها */
.slide-down-enter-active,
.slide-down-leave-active {
  transition: transform 0.3s ease, opacity 0.3s ease;
}
.slide-down-enter-from {
  transform: translateY(-100%);
  opacity: 0;
}
.slide-down-enter-to {
  transform: translateY(0);
  opacity: 1;
}
.slide-down-leave-from {
  transform: translateY(0);
  opacity: 1;
}
.slide-down-leave-to {
  transform: translateY(-100%);
  opacity: 0;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s ease;
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>
