<script setup lang="ts">
const showCartDropdown = ref(false)
const showCartOffcanvas = ref(false)
const showMobileMenu=ref(false)
const toggleCart = () => {
  if (window.innerWidth >= 640) {
    showCartDropdown.value = !showCartDropdown.value
    showMobileMenu
  } else {
    showCartOffcanvas.value = true
  }
}

const closeCart = () => {
  showCartOffcanvas.value = false

}

// ⛔️ بستن dropdown ها وقتی بیرون کلیک میشه
onMounted(() => {
  document.addEventListener('click', (e) => {
    if (!e.target.closest('#menu-wrapper')) {
      showCartDropdown.value = false
      showCartOffcanvas.value = false
    }

  })
})
</script>

<template>
  <div id="menu-wrapper" class="py-4 relative  px-3 mx-1 rounded-md  hover:bg-gray-500"  @click="toggleCart">

  <!-- Desktop Cart Dropdown -->
  <transition name="fade-slide">
    <div v-if="showCartDropdown" class="fixed  mt-2 dark:bg-neutral-800 w-96 bg-white  rounded-lg shadow-2xl z-50 p-4 hidden sm:block">
      <ul>
        <li>دسته بندی ۱</li>
        <li>دسته بندی ۱</li> <li>دسته بندی ۱</li>
        <li>دسته بندی ۱</li> <li>دسته بندی ۱</li> <li>دسته بندی ۱</li> <li>دسته بندی ۱</li>
        <li>دسته بندی ۱</li>
      </ul>
    </div>
  </transition>
  <!-- Mobile Cart Offcanvas -->
  <transition name="slide-right">
    <div v-if="showCartOffcanvas" class="fixed top-0 right-0 w-80 h-screen dark:bg-neutral-900 bg-white z-50 shadow-lg overflow-y-auto p-2 block sm:hidden">
      <div class="p-4 flex justify-between items-center border-b">
        <button @click="closeCart">✖️</button>
      </div>
      <ul>
        <li>دسته بندی2۱</li>
        <li>دسته بندی ۱</li> <li>دسته بندی ۱</li>
        <li>دسته بندی ۱</li> <li>دسته بندی ۱</li> <li>دسته بندی ۱</li> <li>دسته بندی ۱</li>
        <li>دسته بندی ۱</li>
      </ul>
    </div>
  </transition>

    <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" class="" viewBox="0 0 24 24" stroke="currentColor" stroke-width="1.2" stroke-linecap="round" fill="none" role="img" aria-label="menu">
      <line x1="4" y1="8" x2="20" y2="8" />
      <line x1="18" y1="16" x2="8" y2="16" />
    </svg>
  </div>

  <transition name="fade">
    <div
        v-if="showCartOffcanvas"
        class=" h-screen fixed inset-0 bg-black bg-opacity-40 z-40"

    ></div>
  </transition>
</template>

<style scoped>
fade-slide-enter-active, .fade-slide-leave-active {
  transition: opacity 0.3s ease, transform 0.3s ease;
}
.fade-slide-enter-from, .fade-slide-leave-to {
  opacity: 0;
  transform: translateY(100%);
}
.fade-slide-enter-to, .fade-slide-leave-from {
  opacity: 1;
  transform: translateY(0%);
}

.slide-right-enter-active, .slide-right-leave-active {
  transition: transform 0.3s ease, opacity 0.3s ease;
}
.slide-right-enter-from, .slide-right-leave-to {
  transform: translateX(8%);
  opacity: 0;
}
.slide-right-enter-to, .slide-right-leave-from {
  transform: translateX(0);
  opacity: 1;
}

.fade-enter-active, .fade-leave-active {
  transition: opacity 0.3s ease;
}
.fade-enter-from, .fade-leave-to {
  opacity: 0;
}

</style>