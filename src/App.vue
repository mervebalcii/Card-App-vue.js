<template>
  <div class="container">
    <h3>Card App</h3>
    <hr>
    <appCardComp :initialData="cardData"></appCardComp>
  </div>
</template>

<script>
import CardComp from "./components/CardComp.vue";

export default {
  components: {
    appCardComp: CardComp
  },
  data() {
    return {
      cardData: {
        selectedFiles: [],
        title: "",
        message: "",
        isSubmitted: false
      }
    };
  }
};
</script>

<style>
</style>
