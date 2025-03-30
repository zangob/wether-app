<script setup>
import { ref, onMounted } from 'vue';
import axios from 'axios';

const weatherData = ref(null);
const temperature = ref('--');
const windSpeed = ref('--');
const hide = ref(false);
const fetchWeatherData = async () => {
  try {
    const response = await axios.get('https://api.open-meteo.com/v1/forecast?latitude=52.52&longitude=13.41&current=temperature_2m,wind_speed_10m&hourly=temperature_2m,relative_humidity_2m,wind_speed_10m');
    weatherData.value = response.data;
    temperature.value = Math.round(response.data.current.temperature_2m);
    windSpeed.value = response.data.current.wind_speed_10m;
  } catch (error) {
    console.error('Error fetching weather data:', error);
  }
};

onMounted(() => {
  fetchWeatherData();
  setTimeout(() => {
    const loader = document.querySelector('.loader');
    loader.classList.add('scoop');
  }, 2700);
  setTimeout(() => {
    hide.value = true;
    document.body.style.backgroundColor = 'transparent';

  }, 3500);

});
</script>

<template>
      <!-- <div id="Weather"> -->
        <div class="loader">
            </div>
            <div class="r" v-show="hide"></div>
            <div class="l" v-show="hide"></div>
            <div class="t" v-show="hide"></div>
            <div class="e" v-show="hide"></div>
            <div class="c" v-show="hide"></div>
            <div class="s" v-show="hide">{{ temperature }}°</div>
            <div class="w" v-show="hide">wind speed:</div>
            <div class="h" v-show="hide">{{ windSpeed }}Km/h</div>

    <!-- </div>   -->

</template>

<style>
body{
    background-color: black;
    color: #fff;
    font-family: Arial, Helvetica, sans-serif;
    margin: 0;
    padding: 0;
}
.t{
  position: relative;
  width: 300px;
  height: 300px;
  top: -61vmax;
  left: 0vmax;
  background-color: rgb(0, 204, 255);
  border-radius: 0 0 300px 0;
  z-index: 100;
  animation: dis 5.5s linear ;
}
.s{
  position: relative;
  width: 300px;
  height: 350px;
  top: -100vmax;
  left: 45vmax;
  border-radius: 15%;
  font-size: 290px;
  color:black;
  animation: dis 4s  ;

}
.w{
  position: relative;
  width: 900px;
  height: 350px;
  top: -100vmax;
  left: 26vmax;
  font-size: 90px;
  color:rgb(0, 0, 0);
  text-align: center;
  animation: dis 4.5s  ;

}
.h{
  position: relative;
  width: 900px;
  height: 350px;
  top: -110vmax;
  left: 26vmax;
  font-size: 200px;
  color:rgb(0, 0, 0);
  text-align: center;
  animation: dis 4.5s  ;
}
.e{
  position: relative;
  width: 300px;
  height: 300px;
  top: -66vmax;
  left: -12vmax;
  background-color: white;
  border-radius: 300px 0 ;
  z-index: 1000;
  transform: rotate(26deg); 
  animation: dis 1s  ;
}
.c{
  position: relative;
  width: 300px;
  height: 300px;
  top: -88vmax;
  left: 5vmax;
  background-color: white;
  border-radius: 50%;
  z-index: 10000; 
  animation: dis 100ms linear ;
}
.r{
  position: relative;
  width: 500px;
  height: 500px;
  top: 26vmax;
  left: -2vmax;
  background-color: whitesmoke;
  border-top-right-radius: 2000px;
  z-index: 1000;
  box-shadow: 0 0 100px rgba(0, 0, 0, 0.5);
  animation: dis 2.5s linear ;
}
.l{
  position: relative;
  width: 500px;
  height: 500px;
  top: -6vmax;
  right: -76vmax;
  background-color: whitesmoke;
  border-top-left-radius: 2000px;
    z-index: 1000;
    box-shadow: 0 0 100px rgba(0, 0, 0, 0.5);
    animation: dis 2.5s linear ;


}
/* #Weather{
    display: relative;
    background-color: #0abeeb;
    width: 300px;
    height: 400px;
    margin: 50px auto;
    top: 100px;
    right: -300px;
    padding: 20px;
    border-radius: 10px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.5);
} */

.loader {
    position: relative;
    width: 110px;
    height: 30px;
    top: 23vmax;
    right: -47vmax;
    background: #fff;
    border-radius: 100px;
    animation: moving 2s linear ;
    transition: transform 3s ease;

  }
  @keyframes moving{
    0%{
        right: 10vmax;
    }
    100%{
        right: -47vmax;
    }
  }
  .loader::before{
    content: '';
    position: absolute;
    top: -20px;
    left: 10px;
    width: 30px;
    height: 30px;
    background: #fff;
    border-radius: 50%;
    box-shadow: 40px 0 0 20px #fff;
    
  }
  .scoop{
    transform: scale(400);

  }
  @keyframes dis{
    0%{
          opacity: 0;
    }
    100%{
        opacity: 1;
    }
  }
  /* .snow {
    position: relative;
    display: flex;
    z-index: 1;
  } */
  
  .snow span {
    position: relative;
    width: 3px;
    height: 3px;
    background: #fff;
    margin: 0 2px;
    border-radius: 50%;
    /* animation: snowing 15s linear infinite;
    animation-duration: calc(15s / var(--i));
    transform-origin: bottom; */
  }
  
  /* @keyframes snowing {
    0% {
      transform: translateY(0px);
    }
  
    70% {
      transform: translateY(200px) scale(1);
    }
  
    100% {
      transform: translateY(200px) scale(0);
    }
  } */



</style>
