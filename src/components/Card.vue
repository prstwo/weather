<template>
  <div>
    <div class="max-w-sm rounded overflow-hidden shadow-lg">
      <img class="w-full" src="weather.jpg" alt="Sunset in the mountains">
      <div class="px-6 py-4">
        <div class="font-bold text-xl mb-2">The Coldest Sunset</div>
        <p class="text-gray-700 text-base">
          Lorem ipsum dolor sit amet, consectetur adipisicing elit. Voluptatibus quia, nulla! Maiores et perferendis eaque, exercitationem praesentium nihil.
        </p>
      </div>
      <div class="px-6 pt-4 pb-2">
        <span class="inline-block bg-gray-200 rounded-full px-3 py-1 text-sm font-semibold text-gray-700 mr-2 mb-2"></span>
      </div>
      <form action="" @submit.prevent="fetchApi">
        <input type="text" @v-model="city" placeholder="enter city name">
        <input type="submit" value="Send">
      </form>
      <div class="show-info" v-if="!isLoading">
        <ul>
          <li>

          </li>
        </ul>
      </div>
    </div>
  </div>
</template>
<script>
import axios from 'axios';
 const key ='ac89a533b6e0b6c6f66719241b35ea45';
 export default {
   name:"Card",
   data(){
     return{
       city:null,
       info:{},
       isLoading:false
     }
   },
   methods:{
     fetchApi(){
       this.isLoading=true;
       axios.get(`https://api.openweathermap.org/data/2.5/weather`,
           {
             params:{
               q:this.city,
               appid: key,
               units:'metric'
             }
           });
     }
   }
 }
</script>
<style></style>