<template>
  <div v-bind:class="{ active : isActive }" class="circle">
    <span class="img-content">
      <img :src="imgBall" class="8ball" /> 
      <p v-bind:class="{ delayFade : isDelayFade, resetFade : isResetFade }"> {{ answer }} </p>
    </span>
  </div>
</template>

<script>
import imgBall from "../assets/8ball.png";
const answers = [
  "It is certain",
  "It is decidedly so",
  "Without a doubt",
  "Yes - definitely",
  "You may rely on it",
  "As I see it, yes",
  "Most likely",
  "Outlook good",
  "Yes",
  "Signs point to yes",
  "Don't count on it",
  "My reply is no",
  "My sources say no",
  "Outlook not so good",
  "Very doubtful",
  "Reply hazy, try again",
  "Ask again later",
  "Better not tell you now",
  "Cannot predict now",
  "Concentrate and ask again",
];
export default {
  name: "Answer",
  props: {
    question: {
      type: String,
      required: false,
      default: null
    }
  },
  data() {
    return {
      imgBall:"",
      answer:"",
      isActive: false,
      isDelayFade: false,
      isResetFade: true,
    }
  },
  methods: {
    getAnswer() {
      if (!this.question) {
        return;
      }
      const index = Math.floor(Math.random() * answers.length);
      this.answer = answers[index];
      this.imgBall = imgBall;
      this.isActive = true;
      this.isDelayFade = true;
      this.isResetFade = false;
      //view answer in console
      console.log(this.answer);
    },
  },
  watch: {
    question: {
      handler() {
        this.getAnswer();
      },
      immediate: true,
    }
  },
}
</script>
<style lang="scss">
  @import "../scss/variables.scss";
  @import "../scss/mixins.scss"; 
  .circle {
    display: flex;
    justify-content: center;
    align-items: center;
    padding-top:30px;
    padding-bottom:20px;
    .img-content {
      display: contents;
      img {
        max-width:333px;
      }
      p {
        opacity:0;
        position:absolute;
        max-width:60px;
        max-height:40px;
        text-align:center;
        display:grid;
        flex-direction: column;
        justify-content:center;
        font-size:$size2;
        margin-top:16px;
      }
      p.resetFade {opacity:0;}
      p.delayFade {
        opacity:1;
        animation: delayFade 2000ms ease;
        -webkit-animation: delayFade 2000ms ease;
      }
      @keyframes delayFade {
        0% {
          opacity: 0;
        }
        60% {
          opacity:0;
        }
        100% {
          opacity:1;
        }
      }
    }
  }
  .active {
    opacity:1;
    animation: active 950ms ease-in-out;
    -webkit-animation: active 950ms ease-in-out; 
  }
  @keyframes active {
    0% {
      opacity: 0;
      -webkit-transform: translateX(40px);
    }
    5% {
      -webkit-transform: translateX(0px);
    }
    10% {
      -webkit-transform: translateX(-40px);
    }
    15% {
      -webkit-transform: translateX(0px);
    }
    20% {
      -webkit-transform: translateX(40px);
    }
    25% {
      -webkit-transform: translateX(0px);
    }
    30% {
      -webkit-transform: translateX(-40px);
    }
    35% {
      -webkit-transform: translateX(0px);
    }
    40% {
      -webkit-transform: translateX(40px);
    }
    45% {
      -webkit-transform: translateX(0px);
    }
    50% {
      -webkit-transform: translateX(-40px);
    }
    55% {
      -webkit-transform: translateX(0px);
    }
    60% {
      -webkit-transform: translateX(40px);
    }
    65% {
      -webkit-transform: translateX(0px);
    }
    70% {
      -webkit-transform: translateX(-40px);
    }
    75% {
      -webkit-transform: translateX(0px);
    }
    100% {
        opacity: 1;
    }
  }
  // X-Small devices (portrait phones, less than 576px)
  @media (max-width: 575.98px) {
    .circle > .img-content > p {
      max-width:57px;
      margin-top:2px;
    }
  }
</style>