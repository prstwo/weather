<template>
  <div class="flex flex-col justify-center align-center items-center h-full">
    <div class="max-w-sm rounded overflow-hidden shadow-lg  m-1">
      <img class="w-full" src="weather.jpg" alt="Sunset in the mountains">
      <div class="px-6 py-6">
        <div class="pb-4">
          <div class="font-bold text-xl mb-2">Weather Forecast</div>
          <p class="text-gray-700 text-base">
            Lorem ipsum dolor sit amet, consectetur adipisicing elit. Voluptatibus quia, nulla! Maiores et perferendis eaque, exercitationem praesentium nihil.
          </p>
        </div>
        <div class="pt-4 pb-2">
          <span class="inline-block bg-gray-200 rounded-full px-3 py-1 text-sm font-semibold text-gray-700 mr-2 mb-2"></span>
        </div>
        <form action=""  >
          <Map @sendCoord="fetchMapCoord"/>
        </form>
        <div class="pt-4">
          <div class="show-info" v-if="!isLoading&&!info.isEmpty" >
            <ul>
              <template v-for="(result, index) in info" :key="index">
                <li class="mb-2">
                  <span class="pr-1 opacity-80">{{result[0]}}:</span>
                  <span>
                    {{result[1]}}
                  </span>
                </li>
              </template>

            </ul>
          </div>
          <div v-else-if="isLoading">
            <p class="animate-pulse">
              Getting info...
            </p>
          </div>
        </div>
      </div>
      <Footer />
    </div>

  </div>
</template>
<script>
import axios from 'axios';
import Map from './Map'
import Footer from "./Footer";
/*end of imports*/
 const key ='ac89a533b6e0b6c6f66719241b35ea45';
 export default {
   name:"Card",
   components:{Footer, Map},
   data(){
     return{
       city:null,
       info:{city: ['City',''], desc:  ['Description',''], wind: ['Wind Speed',''], temp: ['Tempreture',''], isEmpty:true },
       isLoading:false,
       test:null

     }
   },
   methods:{
     fetchMapCoord(latlon){
       console.log(latlon);
       this.isLoading=true;
       axios.get('https://api.openweathermap.org/data/2.5/weather?', {
         params: {
           appid: key,
           lat:latlon[1],
           lon:latlon[0],
           units:'metric'

         }
       }).then(({data})=>{
         this.info.isEmpty = false;
         console.log(data)
         this.info.city[1] = data.name;
         this.info.temp[1] = data.main.temp + '°C';
         this.info.desc[1] = data.weather[0].description ;
         this.info.wind[1] = data.wind.speed;
         this.isLoading=false;
       })
     }
   }
 }
</script>
<style></style>