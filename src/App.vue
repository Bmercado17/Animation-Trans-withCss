


<template>
  <button type="button" @click="flag = !flag">Toggle Ani</button>
  <!-- because of the name 'fade' in the transition tag, is targeted as a class inthe css  -->
  <transition name="fade">
    <h2 v-if="flag">Animate</h2>
  </transition>
</template>
  <!--  vue logic  -->

<script>
  export default {
    name: 'App',
    data(){
      // to create the toggle effect connected with the button flag starts as false and toggles with statement at button
      return{
        flag: false,
      }
    }
  }

</script>

<style>
  .fade-enter-from {
    opacity: 0;
  }
  .fade-enter-active {
    transition: all 0.45s linear;
  }
  .fade-leave-to {
    transition: all .45s linear;
    opacity: 0;
  }
</style>

