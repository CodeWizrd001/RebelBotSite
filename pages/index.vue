<template>
  <div>
    <div class="wrap">
      <div v-for="index in 144" :key="index" class="c"></div>
    </div>
      <div class="center-box">
        <div class="title">
          <h1>Rebel Bot</h1>
        </div>
        <div class="button-box">
            <a href="https://discord.com/api/oauth2/authorize?client_id=890971754401525770&permissions=515433291328&scope=bot" target="_blank">
              <button class="button2">
                <span></span>
                <span></span>
                <span></span>
                <span></span>
                Invite
              </button>
            </a>
            <a href="https://discord.com/invite/wPYnTrXnz3" target="_blank">
              <button class="button2">
                <span></span>
                <span></span>
                <span></span>
                <span></span>
                Support
              </button>
            </a>
          </div>
      </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({})
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css?family=Montserrat');
  body {
    background-color: #111;
  }

  .title {
    font-family: "Montserrat";
    text-align: center;
    color: #FFF;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 36vh;
    min-height: 180px;
    min-width: 250px;
    letter-spacing: 1px;
    z-index: 1;
    position: relative;
    background-color: rgba(59, 27, 117, 0.5);
    border-radius: 10px;
    padding: 10px;
  }

  h1 {
    background-image: url(https://media.giphy.com/media/26BROrSHlmyzzHf3i/giphy.gif);
    background-size: cover;
    color: transparent;
    -moz-background-clip: text;
    -webkit-background-clip: text;
    text-transform: uppercase;
    font-size: calc(max(18vh,70px));
    line-height: .75;
    margin: 2px 0;
  }

  @media screen and (max-width: 1000px) {
    h1 {
      font-size: calc(max(12vh,70px));
    }

    .title {
      height: 30vw;
    }
  }

  .button {
    margin: 10px;
  }

  .center-box {
    width: 50vw;
    margin: 25vh auto;
    text-align: center;
  }

  .button-box {
    justify-content: space-around;
  }

  .grid-container {
    display: grid;
    grid-template: repeat(12, 1fr) / repeat(12, 1fr);
  }
</style>

<style lang="scss" scoped>

.button2 {
  background-color: black;
  position: relative;
  display: inline-block;
  padding: 30px 61px;
  border-radius: 4px;
  color: #03e9f4;
  text-decoration: none;
  text-transform: uppercase;
  overflow: hidden;
  margin: 25px;
  font-family: "Roboto", sans-serif;
  filter: hue-rotate(0deg);
  border: 2px solid #d2bdff;
  transition: all 0.1s linear;

  &:hover {
    border: 1px solid transparent;
    span {
      position: absolute;
      display: block;

      &:nth-child(1) {
        filter: hue-rotate(0deg);
        top: 0;
        left: 0;
        width: 100%;
        height: 3px;
        background: linear-gradient(90deg, transparent, #3a86ff);
        animation: animate1 1s linear infinite;
      }
      @keyframes animate1 {
        0% {
          left: -100%;
        }
        50%,
        100% {
          left: 100%;
        }
      }

      &:nth-child(2) {
        filter: hue-rotate(60deg);
        top: -100%;
        right: 0;
        width: 3px;
        height: 100%;
        background: linear-gradient(180deg, transparent, #3a86ff);
        animation: animate2 1s linear infinite;
        animation-delay: 0.25s;
      }

      @keyframes animate2 {
        0% {
          top: -100%;
        }
        50%,
        100% {
          top: 100%;
        }
      }
      &:nth-child(3) {
        filter: hue-rotate(120deg);
        bottom: 0;
        right: 0;
        width: 100%;

        background: linear-gradient(270deg, transparent, #3a86ff);
        animation: animate3 1s linear infinite;
        animation-delay: 0.5s;
      }
      @keyframes animate3 {
        0% {
          right: -100%;
          height: 3px;
        }
        50%,
        100% {
          height: 2px;
          right: 100%;
        }
      }

      &:nth-child(4) {
        filter: hue-rotate(300deg);
        bottom: -100%;
        left: 0;
        width: 3px;
        height: 100%;
        background: linear-gradient(360deg, transparent, #3a86ff);
        animation: animate4 1s linear infinite;
        animation-delay: 0.75s;
      }
      @keyframes animate4 {
        0% {
          bottom: -100%;
        }
        50%,
        100% {
          bottom: 100%;
        }
      }
    }
  }
}
</style>

<style lang="scss">
$total: 144;
$time: 4;
$height: 400;
$percent: .69444%;
$dotSize: .6;

* {
  box-sizing: border-box;
}

html, body {
  height: 100%;
}

body {
  background: black !important;
  overflow: hidden;
}

.wrap {
  position: relative;
  height: 100%;
  z-index: -2;
}

.c {
  position: relative;
  height: $height+px;
  width: $percent;
  margin-top: -$height+px;
  animation: drop $time+s infinite ease-in;
  z-index: -1;
  &:after {
    content: "";
    position: absolute;
    width: $dotSize+vw;
    height: $dotSize+vw;
    border-radius: 50%;
    left: 50%;
    bottom: -($dotSize/2)+vw;
    margin-left: -($dotSize/2)+vw;
  }
}

@for $i from 1 through $total {
  $hue: (300/$total) * $i;
  .c:nth-child(#{$i}){
    left: ($i - 1) * $percent;
    background-image: linear-gradient( to bottom, black, hsla($hue, 100%, 50%, .8));
    animation-delay: random($total) * ($time/$total) * -1s;
    &:after {
      background: hsla($hue, 100%, 50%, 1);
    }
  }
}

@keyframes drop {
  80% {
    opacity: 1;
  }
  100% {
    transform: translate3d(0, 150vh, 0);
    opacity: 0;
  }
}
</style>