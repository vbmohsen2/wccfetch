<template>
  <div class="min-h-screen transition-colors duration-300
           bg-white text-gray-900
           dark:bg-black/95 dark:text-white" dir="rtl">
    <!-- هدر سایت -->
   <Header/>

    <!-- محتوای هر صفحه -->
    <main class=" relative p-6 pt-48">
      <slot />
    </main>

    <!-- فوتر -->
    <footer class=" p-4 text-center">
      <p>© 2025 همه حقوق محفوظ است</p>
    </footer>
  </div>
</template>
