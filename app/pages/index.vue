<script setup lang="ts">
import heroImage from '~/assets/media/nvidia.png';
const myPost = {
  title: 'شستنیانتش شمسنتیمن شستیمتسشمن یتشس مینساخت کامپوننت‌های ریسپانسیو',
  author: 'جمینی',
  image: heroImage,
  comments: 34,
  age: '1 ساعت پیش'
};
</script>

<template>
<div class="max-w-screen-xl mx-auto container ">
   
    <section class=" grid md:grid-cols-2 sm:grid-cols-1 md:gap-8  my-9 mx-4 overflow-hidden">
        <post-prominent :post="myPost">
                
        </post-prominent>
         <post-prominent :post="myPost">
                
        </post-prominent >
       <post :post="myPost"/>
      <post :post="myPost"/>
      <post :post="myPost"/>
      <post :post="myPost"/>
      <post :post="myPost"/>
      <post :post="myPost"/>
      <post :post="myPost"/>
      <post :post="myPost"/>
      <post :post="myPost"/>



        
    </section>
</div>
</template>

<style scoped>

</style>