<script setup>
import { ref } from "vue";
import { useRouter } from "vue-router";

const router = useRouter();
const showFirstContainer = ref(true);
const yesButtonScale = ref(1);
const noButtonTexts = ["No :<", "Sure nana ling?", "di najd mahanyo :<", "Last najud!", "ling please :<", "mo iyak nako! 😢", "huhuhu"];
const noClickCount = ref(0);
const noButtonPosition = ref({ top: 0, left: 0 });
const showNoButton = ref(true); // Track visibility of the No button

const toggleContainer = () => {
  showFirstContainer.value = !showFirstContainer.value;
};

const enlargeYesButton = () => {
  if (noClickCount.value < 6) {
    yesButtonScale.value += 1.5;
    noClickCount.value++;

    // Move the No button randomly
    noButtonPosition.value = {
      top: Math.random() * 200 - 100 + "px",
      left: Math.random() * 200 - 100 + "px",
    };
  }

  // Hide the No button after 6 clicks
  if (noClickCount.value >= 6) {
    showNoButton.value = false;
  }
};
</script>

<template>
  <div class="container">
    <!-- First Container -->
    <div v-if="showFirstContainer" class="first-container" @click="toggleContainer">
      <img src="@/assets/miming.png" alt="miming" />
      <p class="text-name">For Langling <33</p>
    </div>

    <!-- Second Container -->
    <div v-else class="second-container">
      <div class="sub-container">
        <img src="@/assets/miming2.png" alt="miming2" />
        <p class="text-title">Will you <br /> be my <br /> valentine??</p>
        <div class="btns">
          <button class="yes" :style="{ transform: `scale(${yesButtonScale})` }" @click="router.push('/yes')">Yes!</button>
          <button 
            v-if="showNoButton"
            class="no" 
            @click="enlargeYesButton" 
            :style="{ transform: `translate(${noButtonPosition.left}, ${noButtonPosition.top})` }"
          >
            {{ noButtonTexts[noClickCount] }}
          </button>

        </div>
      </div>
    </div>
  </div>
</template>

<style scoped lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Marck+Script&display=swap");
@import url("https://fonts.googleapis.com/css2?family=Lobster&family=Marck+Script&display=swap");

.container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  margin: 0 auto;
  overflow-y: hidden;
  
  @media screen and (max-width: 600px) {
    margin: 0px 10px;
  }
}

.first-container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  width: 800px;
  height: 450px;
  background-color: #ffb3c6;
  cursor: pointer;
  border-radius: 50px;

  @media screen and (max-width: 600px) {
    width: 400px;
    height: 400px;
    margin: 15px;
  }

  .text-name {
    color: white;
    font-size: 50px;
    font-family: "Marck Script", serif;
    font-weight: 400;
    font-style: normal;

    @media screen and (max-width: 600px) {
      font-size: 30px;
    }
  }

  img {
    width: 200px;
    height: 200px;
    border-radius: 50px;

    @media screen and (max-width: 600px) {
      width: 100px;
      height: 100px;
    }
  }
}

.second-container {
  display: flex;
  width: 500px;
  height: 600px;
  background-color: red;
  cursor: pointer;
  border-radius: 50px;
  position: relative;
  overflow: hidden;

  @media screen and (max-width: 600px) {
    width: 350px;
    margin: 10px;
  }

  /* Flickering Heart Background */
  &::before {
    content: "❤";
    font-size: 200px;
    color: rgba(255, 255, 255, 0.6);
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    animation: flicker 1.5s infinite alternate ease-in-out;
  }
}

@keyframes flicker {
  0% {
    opacity: 0.3;
    transform: translate(-50%, -50%) scale(1);
  }
  50% {
    opacity: 1;
    transform: translate(-50%, -50%) scale(1.1);
  }
  100% {
    opacity: 0.3;
    transform: translate(-50%, -50%) scale(1);
  }
}

.sub-container {
  display: flex;
  flex-direction: column;
  margin: 50px 20px;
  padding: 20px;
  cursor: pointer;
  border-radius: 50px;
  position: relative;

  img {
    width: 200px;
    height: 200px;
    border-radius: 50px;
    position: absolute;
    left: 60%;
    top: -10px;

    @media screen and (max-width: 600px) {
      width: 200px;
      height: 200px;
      left: 50%;
      top: 5px;
    }
  }

  .text-title {
    color: white;
    font-size: 60px;
    font-family: "Lobster", serif;
    font-weight: 600;
    font-style: normal;
  }

  .btns {
    display: flex;
    margin-top: 150px;
    justify-content: space-between;
    position: relative;

    .yes {
      margin: 10px;
      padding: 10px 20px;
      border: none;
      border-radius: 5px;
      background-color: white;
      color: red;
      font-size: 20px;
      font-weight: bold;
      cursor: pointer;
      transition: transform 0.3s ease-in-out;
    }

    .no {
      margin: 10px;
      margin-left: 150px;
      padding: 10px 20px;
      border: none;
      border-radius: 5px;
      background-color: white;
      color: red;
      font-size: 20px;
      font-weight: bold;
      cursor: pointer;
      position: relative;
      transition: transform 0.5s ease-in-out;

      @media screen and (max-width: 600px) {
        margin-left: 75px;
      }
    }
  }
}
</style>
