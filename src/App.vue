<template>
  <!-- <TheFloor></TheFloor> -->
  <ElevatorShaft></ElevatorShaft>
  <!-- <TheElevator></TheElevator> -->
</template>

<script>
// import TheElevator from './components/TheElevator.vue';
import ElevatorShaft from './components/ElevatorShaft.vue';
// import TheFloor from './components/TheFloor.vue';

export default {
  name: 'App',
  components: {
  // TheElevator,
    ElevatorShaft,
    // TheFloor
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
/* App.vue 
.elevator-shaft {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  ;
}

.elevator {
  width: 100px;
  height: 200px;
  background-color: #333;
  color: #fff;
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 5px;
}

.floor {
  margin: 10px;
}

.button {
  padding: 10px;
  background-color: #ccc;
  color: #333;
  border: none;
  border-radius: 5px;
}

.button.active {
  background-color: yellow;
}

.button.green {
  background-color: green;
}
*/</style>
