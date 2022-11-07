<!-- Create a childcomponent - DragonComp.vue -->
<!-- Send dragondata from App.vue to DragonComp as a prop -->
<!-- Build a simple dragon template in DragonComp where you show: Name, Skills, Challenge and display the img_url -->
<!-- Create an input field below the dragon with a label:
  <form>
    <label for="betterName">Rename to:</label>
    <input type="text" placeholder="Better name..." id="betterName" required>
    <input type="submit" value="Update name" />
  </form>
-->
<!-- Bind the input to a value in props -->

<template>
  <div>
    <DragonComp

    @myCustomEvent="eventFromChild"

     v-for="dragon in dragons" 
     :key="dragon.name" 
     :dragon="dragon"
     ></DragonComp>
  </div>
</template>

<script>
import dragons from '@/assets/dragons';
import DragonComp from './components/DragonComp.vue';

export default {
  name: "App",
  data() {
    return {
      dragons,
    };
  },
  components: {DragonComp},

  methods: {
    eventFromChild(oldName, newName){
      this.dragons.forEach((dragon) => {
        if(dragon.name === oldName){
          dragon.name= newName;
        }
      })
    },
  },
};
</script>

<style>
#app {

}
</style>
