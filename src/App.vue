<script>
import LigthBulb from "./components/LigthBulb.vue";
export default {
  data(){
      return{
          lucesEncendidas: 0,
          luces:[1,2]
      }
  },
  components:{
    LigthBulb
  }
};
</script>

<template>  
  <main>
    <!-- Mensaje -->
    <h1>Rama master</h1>

    <h1 v-if="lucesEncendidas < this.luces.length">Pulsa en las bombillas el numero que te indican para encenderlas</h1>
    <h1 v-else>Todas las bombillas han sido encendidas</h1>

    <!-- Bombillas -->
    <div class="flex-grid">
      <div v-for="(luz, indx) in luces" v-bind:key="indx">
        <ligth-bulb @switchedOn="(num) => lucesEncendidas += num" :necessaryClicks="luz"/>
      </div>            
    </div>
  </main>
</template>

<style>
@import './assets/base.css';

.flex-grid{
  display: flex;
  flex-wrap: wrap;
  flex-direction: row;
  justify-content: center;
}

#app {
  font-weight: normal;
}
h1{
  text-align: center;
  user-select: none;
}
</style>
