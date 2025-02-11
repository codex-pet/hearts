<script setup>
import { ref } from "vue";
import { useRouter } from "vue-router";

const router = useRouter();



</script>

<template>
  <div class="container">
    <!-- First Container -->
     
    <div class="first-container" >
      <p class="text-name">YEYEYEYYY!!🥰🥰</p>
      <p class="text-name">LABYUULABYUU😘</p>
      <p class="text-name">BABYYYY!!!💞💞</p>

      <div class="miming">
        <img class="miming1" src="@/assets/mimingjump.gif" alt="miming" />
        <img class="miming2" src="@/assets/mimingjump.gif" alt="miming" />
      </div>

    </div>

    
  </div>
</template>

<style scoped lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Itim&family=Lobster&family=Marck+Script&family=Pacifico&family=Shadows+Into+Light&display=swap');



.container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  width: 100%;
  background-color: #ffb3c6;
  margin: 0 auto;

  @media screen and (max-width: 600px) {
    width: 100%;
  }

  .first-container {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    width: 600px;
    // height: 550px;
    cursor: pointer;
    border-radius: 50px;

    @media screen and (max-width: 600px) {
        width: 400px;
        margin-top: 100px;
    }

    .text-name {
      color: white;
      font-size: 60px;
      font-family: "Itim", serif;
      font-weight: 400;
      font-style: normal;
      margin-top:20px;

      @media screen and (max-width: 600px) {
        font-size: 40px;
      }
      @media screen and (max-width: 360px) {
        font-size: 30px;
      }
    }

    .miming {
        @media screen and (max-width: 600px) {
        // display:flex;
        margin-left:40px;
      }
      .miming1 {
        width: 300px;
        height: 300px;
      }
      .miming2 {
        width: 300px;
        height: 300px;
      }
    }
  }

  
}
</style>
