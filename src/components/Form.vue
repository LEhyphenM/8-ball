<template>
  <form @submit.prevent="getAnswer">
    <div>
      <label>{{ questionLabel }}</label>
      <input v-model="question" />
    </div>
    <button type="submit">{{ askBtn }}</button>
  </form>
</template>

<script>
export default {
  name: "Form",
  data() {
    return {
      questionLabel:"Question:",
      askBtn:"Ask Question",
      question:"",
    }
  },
  methods: {
    getAnswer() {
      if (!this.question) return;
      this.$emit('on-submit', this.question)
      //view question in console
      console.log(this.question);
    },
  }
}
</script>
<style lang="scss">
  @import "../scss/variables.scss";
  @import "../scss/mixins.scss";
  form {
    display:grid;
    flex-direction: column;
    width: 100%;
    div {
      margin:7px auto;
      display:grid;
      label {
        @include defaultText();
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
</style>