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
   
    <section class=" grid grid-cols-2 gap-16  my-9 mx-4 overflow-hidden">
        <post-prominent :post="myPost">
                
        </post-prominent>
         <post-prominent :post="myPost">
                
        </post-prominent>
          <post-prominent :post="myPost">
                
        </post-prominent>
          <post-prominent :post="myPost">
                
        </post-prominent>
          <post-prominent :post="myPost">
                
        </post-prominent>
        <post-prominent :post="myPost">
                
        </post-prominent>
        <post-prominent :post="myPost">
                
        </post-prominent>
        <post-prominent :post="myPost">
                
        </post-prominent>
        <post-prominent :post="myPost">
                
        </post-prominent>

        <post-prominent :post="myPost">
                
        </post-prominent>
        <post-prominent :post="myPost">
                
        </post-prominent>

        <post-prominent :post="myPost">
                
        </post-prominent>
        
    </section>
</div>
</template>

<style scoped>

</style>