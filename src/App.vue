


<template>
  <button type="button" @click="flag = !flag">Toggle Ani</button>
  <!-- because of the name 'fade' in the transition tag, is targeted as a class inthe css  -->
  <!-- <transition name="fade" mode="in-out">
    <h2 v-if="flag" key="main" >Animate</h2>

    <h2 v-else key="secondary">Optional Ani</h2>
   
  </transition> -->
  <!-- add 'type to trigger wheter animation or transition' you want to create -->
  <transition name="zoom" type="animation">  
    <h3 v-if="flag">Basic message</h3>
  </transition>
   <!--we can either use v-if or v-show to toggle the effect-->
</template>
  <!--  vue logic  -->

<script>
  export default {
    name: 'App',
    data(){
      // to create the toggle effect connected with the button 'flag starts as false' and toggles with statement at button
      return{
        flag: false,
      }
    }
  }

</script>

<style>
h2 {
  width: 200px;
  padding: 20px;
  margin: 20px;
}
/* animating the transition with duration, setting the transition mode in the template and in the css */
  .fade-enter-from {
    opacity: 0;
  }
  .fade-enter-active {
    transition: all 1s linear;
  }
  .fade-leave-to {
    transition: all 1.5s linear;
    opacity: 0;
  }

  /* frm lne 55 to lne 76 along with the code on lne 13 with name='zoom' which is used as a class creates zoom in n out effect */

  .zoom-enter-active {
    animation: zoom-in 2s linear forwards;
    transition: all 1s linear;
  }
  .zoom-leave-active {
    animation: zoom-out 1.5s linear forwards;
    transition: all 1.5s linear;
  }

  zoom-enter-from {
    opacity: 0;
  }
  zoom-leave-to {
    opacity: 0;
  }
  @keyframes zoom-in {
    from {
      transform: scale(0,0);
    }
    to {
      transform: scale(1,1);
    }
  }
/* zooming in and zooming out with transform nd scale */

  @keyframes zoom-out {
    from {
      transform: scale (1,1);
    }
    to {
      transform: scale(0,0);
    }
  }
</style>

