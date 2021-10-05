<template>
  <div id ="app">
    <Header></Header>
    <Form @on-submit="handleSubmit"></Form>
    <Answer v-if="question" :question="question"></Answer>
    <Footer></Footer>
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Form from "./components/Form.vue";
import Answer from "./components/Answer.vue";
import Footer from './components/Footer.vue';
export default {
  name: "App",
  components: {
    Header,
    Form,
    Answer,
    Footer
  },
  data() {
    return {
      question: ""
    }
  }, 
  methods: {
    handleSubmit(question) {
      this.question = question;
    }
  },
};
</script>

<style lang="scss">
  @import "./scss/variables.scss";
  @import "./scss/mixins.scss";
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
    }
  }
</style>