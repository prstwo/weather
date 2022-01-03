<template>
  <footer class="relative w-full footer-container">
    <div class="w-full">
      <svg width="100%" height="100%" id="svg" viewBox="0 0 1440 400" xmlns="http://www.w3.org/2000/svg" class="transition duration-300 ease-in-out delay-150"><path d="M 0,400 C 0,400 0,200 0,200 C 145.06666666666666,152 290.1333333333333,104 456,128 C 621.8666666666667,152 808.5333333333333,248 976,272 C 1143.4666666666667,296 1291.7333333333333,248 1440,200 C 1440,200 1440,400 1440,400 Z" stroke="none" stroke-width="0" fill="#8ed1fcff" class="transition-all duration-300 ease-in-out delay-150 path-0"></path>
      </svg>
    </div>
    <div class="w-full px-4 pb-4  bg-site-blue">
      <div class="w-full mx-auto  text-center text-gray-900  flex flex-row justify-center items-center">
        <span class="text-sm">Designed with</span>
        <span class="mx-1">
          <img :src="require('@/assets/images/heart.svg')" alt="" class="w-4 h-auto">
        </span>
        <span class="text-sm">
        by Parastoo Alirezazadeh
      </span>
      </div>
    </div>
  </footer>
</template>

<script>
export default {
  name: "footer"
}
</script>

<style scoped>
.bg-site-blue{
  background-color: #8ED1FC;
}

</style>