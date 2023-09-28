<!-- ANIMATION WITH CSS AND JS CHECKING TRANS IN THE CONSOLE -->

<template>
  <!-- b4-enter,enter,ftr-enter//b4-leave,leave,ftr-leave animations vueHooks -->

  
  <!-- <button type="button" @click="flag=!flag">Toggle Ani</button> -->
  <!-- <transition
    @before-enter="beforeEnter"
    @enter="enter"
    @after-enter="afterEnter"
    @before-leave="beforeLeave"
    @leave="leave"
    @after-leave="afterLeave"
    :css="true"
    name="fade"
    >
    <H2 v-if="flag">Animated</H2> -->
  <!-- because of the name 'fade' in the transition tag, is targeted as a class inthe css  -->
  <!-- <transition name="fade" mode="in-out">
    <h2 v-if="flag" key="main" >Animate</h2>

    <h2 v-else key="secondary">Optional Ani</h2>
   
  </transition> -->
  <!-- add 'type to trigger wheter animation or transition' you want to create -->
  <!-- <transition name="zoom" type="animation">  
    <h3 v-if="flag">Basic message</h3> -->
  <!-- </transition> -->
   <!--we can either use v-if or v-show to toggle the effect-->


  <!-- DIFFERENT ANIMATION USING SPLICE, INDEX AND V-FOR  AND TRANSITION-GROUP-->

  <div>
    <button @click="addItem">ADD</button>

  </div>
  <ul>
  <transition-group name="fade">
    <li v-for= "(number, index) in numbers" :key="number"
    @click="removeItem(index)"
    >
    {{ number }}
    </li>
  </transition-group>
  </ul>
</template>
  <!--  vue logic  -->

<script>
  export default {
    name: 'App',
    data(){
      // to create the toggle effect connected with the button 'flag starts as false' and toggles with statement at button
      return{
        flag: false,
        numbers: [1,2,3,4,5],
      }
    },
    methods:{
      beforeEnter(el,done){
          console.log("before enter")
      },
      addItem(){
        let num = Math.floor(Math.random()*100+1);
        let index = Math.floor(Math.random()* this.numbers.length);
        this.numbers.splice(index, 0, num)

      },
      removeItem(index){
        this.numbers.splice(index,1)
      },
      // hook function enter
      enter(el){
        console.log('enter fired',el)

        // let animation = el.animate([{transform: 'scale3d(0,0,0)'},{}],{duration:1000})
        
        // animation.onfinish = ()=>{
        //   done()
        // }
      },
      //hook function ended
      afterEnter(el){
       console.log("after enter",el)
      },
      beforeLeave(el){
        console.log("before leave",el)
      },
      //hook function leave
      leave(el){
        
        console.log("leave",el)
       

        // let animation = el.animate([{},{transform: 'scale3d(0,0,0)'}],{duration:1000})
        
        // animation.onfinish = ()=>{
        //   done()
        // }
      },
      //hook function ended
      afterLeave(el){
      console.log("after leave",el)
      }
    }
  }

</script>

<style>
body {
  background-color: gray;
}
button {
  display: flex;
  justify-content: left;

}
ul,li {
  color: black;
  background-color: orange;
}

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

  .zoom-enter-from {
    opacity: 0;
  }
  .zoom-leave-to {
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

