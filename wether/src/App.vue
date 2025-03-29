<script setup>
import { ref } from 'vue';

const weatherData = ref(null);



</script>

<template>
      <!-- <div id="Weather"> -->
        <div class="loader">
            </div>
            <div class="r"></div>
            <div class="l"></div>


    <!-- </div>   -->

</template>

<style>
body{
    background-color: whitesmoke;
    color: #fff;
    font-family: Arial, Helvetica, sans-serif;
    margin: 0;
    padding: 0;
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
    right: -50vmax;
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
        right: -50vmax;
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
  .loader:hover{
    transform: scale(100.5);

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
