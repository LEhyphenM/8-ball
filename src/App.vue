<template>
  <div id ="app">
    <h1> {{ title }} </h1>
    <form @submit.prevent="getAnswer">
      <div>
        <label>{{ questionLabel }}</label>
        <input v-model="question" />
      </div>
      <button type="submit">{{ askBtn }}</button>
    </form>
    <div class="circle fade">
      <span class="img-content">
        <img :src="imgBall" class="8ball" /> 
        <p> {{ answer }} </p>
      </span>
    </div>
    <h6> {{ footer }} </h6>
  </div>
</template>

<script>
import imgBall from "./assets/8ball.png";
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
  name: "App",
  data() {
    return {
      title: "Magic 8Ball App",
      questionLabel:"Question:",
      askBtn:"Ask Question",
      question: "",
      answer: "",
      imgBall:"",
      footer: "Lauren Elliott-Manheim • 2015-2022 • Ex astris, scientia",
    };
  },
  methods: {
    getAnswer() {
      if (!this.question) {
        return;
      }
      const index = Math.floor(Math.random() * answers.length);
      this.answer = answers[index];
      this.imgBall = imgBall;
    },
  },
};
</script>

<style lang="scss">
  @mixin styleRemoval {
    box-shadow: none;
    outline: none;
    background-color:transparent;
  }
  @mixin defaultText {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color:$text;
  }
  $size1: 8px;
  $size2: 12px;
  $size3: 18px;
  $size4: 24px;
  $size5: 36px;
  $size6: 48px;
  $background:#172626;
  $text:#F2F2F2;
  $primary:#1F7373;
  $accent:#2E8C60;
  $highlight:#5E75F2;
  body {
    margin: 0;
    padding: 0;
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    background-color:$background;
    color: $text;
    #app {
      max-width: 600px;
      margin:10px auto;
      padding: 20px;
      h1, h2, h6, label {
        @include defaultText();
      }
      h1, h2, h6 {
        color:$highlight;
      }
      h1 {
        font-weight: bold;
        font-size: 28px;
        text-align: center;
        margin-bottom:30px;
      }
      h2{
        font-size:22px;
        margin:30px auto 10px;
        border-bottom:1px solid $primary;
        display:inline-block;
        }
      h6 {
        font-weight:400;
        letter-spacing:2.25px;
        text-transform:uppercase;
        padding:16px;
        text-align:center;
      }
      form {
        display: flex;
        flex-direction: column;
        width: 100%;
        div {
          margin:7px auto;
          display:grid;
          label {
            font-size: 14px;
            font-weight: bold;
            display:flex;
            text-indent:6px;
            line-height:15px;
          }
        }
        input,
        button {
          @include styleRemoval();
          font-size: 18px;
          padding-left: $size2;
          padding-right: $size2;
          border-radius: $size1;
          margin-top: $size1;
          margin-bottom: $size2;
          min-width:300px;
        }
        input {
          height: $size5;
          background-color: transparent;
          border:1px solid $primary;
          color: inherit;
          &:focus {
            background-color:$primary;
            transition: all 0.65s ease;
          }
        }
        button {
          height:$size6;
          color:$text;
          background-color: $primary;
          border:1px solid $primary;
          font-weight: bold;
          outline: none;
          border-radius: $size1;
          margin-top:30px;
          margin-left:auto;
          margin-right:auto;
          max-width:100%;
          min-width:300px;
          &:hover {
            cursor:pointer;
            background-color: lighten($primary, 10%);
            transition: all 0.65s ease;
          }
        }
      }
      .fade {
        transition: opacity 0.25s ease-out; 
      }
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
            position:absolute;
            max-width:75px;
            text-align:center;
            display:flex;
            flex-direction: column;
            justify-content:center;
            font-size:$size2;
          }
        }
      }
    }
  }
</style>