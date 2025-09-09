<template>
  <header class=" font-serif w-full fixed top-0 left-0  box-border mx-auto  z-50
               bg-white/60 dark:bg-gray-900/50
               backdrop-blur-sm shadow-sm dark:text-white">
    <div class="flex flex-col lg:max-w-screen-lg   mx-auto p-2">
    <div class="flex justify-between py-2 ">

<!--    hambergermenu-->
      <div class="flex   w-fit flex-nowrap">
      <div class="py-4 px-3 mx-1 rounded-md  hover:bg-gray-500">
        <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" class="" viewBox="0 0 24 24" stroke="currentColor" stroke-width="1.2" stroke-linecap="round" fill="none" role="img" aria-label="menu">
          <line x1="4" y1="8" x2="20" y2="8" />
          <line x1="18" y1="16" x2="8" y2="16" />
        </svg>
      </div>
<!--        {{colorModeTemp}}-->
      <!--  darkmode-->
      <div  @click="toggleDarkMode" class="py-4 px-3 rounded-xl  hover:bg-gray-500">
        <span v-if="colorModeTemp === 'dark'">
              <svg  xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
          <!-- خورشید (Light Mode) -->
          <circle cx="12" cy="12" r="5" />
          <line x1="12" y1="1" x2="12" y2="3" />
          <line x1="12" y1="21" x2="12" y2="23" />
          <line x1="4.22" y1="4.22" x2="5.64" y2="5.64" />
          <line x1="18.36" y1="18.36" x2="19.78" y2="19.78" />
          <line x1="1" y1="12" x2="3" y2="12" />
          <line x1="21" y1="12" x2="23" y2="12" />
          <line x1="4.22" y1="19.78" x2="5.64" y2="18.36" />
          <line x1="18.36" y1="5.64" x2="19.78" y2="4.22" />
        </svg>
        </span>
        <span v-else>

             <svg  xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">

          <path d="M21 12.79A9 9 0 1111.21 3a7 7 0 109.79 9.79z" fill="currentColor" stroke="none"/>
        </svg>
          </span>
      </div>
      </div>



      <!--      main icon-->
      <div class="flex w-fit">
        <div class="flex items-center space-x-2 text-gray-900 dark:text-white">
          <!-- آیکون -->
          <svg xmlns="http://www.w3.org/2000/svg"
               viewBox="0 0 24 24"
               width="36" height="36"
               fill="none" stroke="currentColor" stroke-width="1.4"
               stroke-linecap="round" stroke-linejoin="round">
            <path d="M6.2 5.5 L11.8 3.5 L17.6 5.5 C18.1 5.8 18.4 6.4 18.2 6.9 L16.8 11.6" />
            <path d="M6.2 5.5 L6.2 17.8 C6.2 18.4 6.7 18.9 7.3 18.9 L12 18.9" />
            <path d="M12 18.9 L16.7 18.9 C17.3 18.9 17.8 18.4 17.8 17.8 L17.8 9.9" />
            <path d="M12 4.2 L12 19" />
            <path d="M8.6 10.2 L10.2 11.1" />
            <path d="M15.4 10.2 L13.8 11.1" />
            <path d="M5.5 6.8 L4.2 5.4" />
            <circle cx="4.2" cy="5.4" r="0.6" fill="currentColor" stroke="none"/>
            <path d="M12 4.2 L17.6 6.1 L17.6 17.8 L12 19 Z" fill="currentColor" stroke="none" opacity="0.95"/>
          </svg>

          <!-- متن لوگو -->
          <span class="font-bold text-xl tracking-wide">TechNova</span>
        </div>




      </div>

      <div class="flex flex-nowrap">
        <div>

            <HeaderSearchBar/>
<!--            <svg xmlns="http://www.w3.org/2000/svg"-->
<!--                 viewBox="0 0 24 24"-->
<!--                 width="24" height="24"-->
<!--                 role="img" aria-label="Search"-->
<!--                 fill="none" stroke="currentColor"-->
<!--                 stroke-width="1.3" stroke-linecap="round" stroke-linejoin="round">-->
<!--              <title>search</title>-->
<!--              &lt;!&ndash; دایره ذره‌بین &ndash;&gt;-->
<!--              <circle cx="11" cy="11" r="5.5" />-->
<!--              &lt;!&ndash; دسته ذره‌بین &ndash;&gt;-->
<!--              <line x1="15.5" y1="15.5" x2="18" y2="19" />-->
<!--            </svg>-->
        </div>

<!--      disscusion icon-->
      <div class="cursor-pointer py-4 px-3 mx-1 rounded-xl  hover:bg-gray-500 ">

        <svg xmlns="http://www.w3.org/2000/svg"
             viewBox="0 0 24 24"
             width="24" height="24"
             role="img" aria-label="User"
             fill="none" stroke="currentColor"
             stroke-width="1.3" stroke-linecap="round" stroke-linejoin="round">
          <title>discussion</title>
          <!-- سر -->
          <circle cx="12" cy="8" r="3.2" />

          <path d="M4.5 19c0-2.9 3.6-4.8 7.5-4.8s7.5 1.9 7.5 4.8" />
        </svg>

      </div>
      </div>





    </div>
    
  <div>

<!--  <header-trending></header-trending>-->

  </div>
     
    </div>
 <header-navbar></header-navbar>
  </header>
</template>

<script setup>
import { ref, onMounted,onBeforeUnmount } from 'vue'

// const isDark = ref(false)

// onMounted(() => {
//   // حالت پیش‌فرض مرورگر
//   if (window.matchMedia && window.matchMedia('(prefers-color-scheme: dark)').matches) {
//     isDark.value = true
//     document.documentElement.classList.add('dark')
//   }
// })
const colorMode = useColorMode()
const colorModeTemp=ref(colorMode.preference)

const categories = ref([
  { id: 1, name: "سیاست", children: [
      { id: 11, name: "مجلس" },
      { id: 12, name: "دولت" },
      { id: 13, name: "احزاب" },
    ]
  },
  { id: 2, name: "اقتصاد", children: [
      { id: 21, name: "بازار سرمایه" },
      { id: 22, name: "ارز و طلا" },
      { id: 23, name: "مسکن" },
    ]
  },
  { id: 3, name: "ورزش", children: [
      { id: 31, name: "فوتبال" },
      { id: 32, name: "والیبال" },
      { id: 33, name: "بسکتبال" },
    ]
  },
  { id: 4, name: "فرهنگ و هنر" },
  { id: 5, name: "علم و فناوری", children: [
      { id: 51, name: "هوش مصنوعی" },
      { id: 52, name: "فضا" },
    ]
  },
  { id: 6, name: "سلامت" },
  { id: 7, name: "محیط زیست" },
  { id: 8, name: "بین‌الملل" },
  { id: 9, name: "اجتماعی" },
  { id: 10, name: "حوادث" }
])
function toggleDarkMode() {
  colorMode.preference = colorMode.preference === 'dark' ? 'light' : 'dark'
  colorModeTemp.value=colorMode.preference

}



const showBanner = ref(true)

const handleScroll = () => {
  showBanner.value = window.scrollY < 20 // کمتر از 20px بنر دیده بشه
}

onMounted(() => window.addEventListener("scroll", handleScroll))
onBeforeUnmount(() => window.removeEventListener("scroll", handleScroll))
</script>

<style>
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