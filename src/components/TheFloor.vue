// TheFloor.vue
<template>
  <div class="floor">
    <button 
      :class="[floorNumber === currentFloor ? 'green' : callMade ? 'active' : 'button']" 
      @click="callElevator">
      {{ floorNumber === currentFloor ? 'Elevator here' : 'Call Elevator to Floor ' + floorNumber }}
    </button>
  </div>
</template>



<script>
export default {
  props: ['floorNumber', 'currentFloor'],
  data() {
    return {
      callMade: false
    }
  },
  methods: {
    callElevator() {
      this.callMade = true;
      this.$emit('callElevator', this.floorNumber);

      // Reset button state after elevator arrives
      setTimeout(() => {
        this.callMade = false;
      }, 5000); // Adjust the timeout based on your elevator movement time
    }
  }
};
</script>

<style scoped>
.floor {
  border:  1px dotted black;
  padding: 50px;
  display: flex;
  justify-content: center;
  background-color: gray;

}

.button {
  width: 175px;
  padding: 10px;
  background-color: #ccc;
  color: #333;
  border: none;
  border-radius: 5px;
}

.active {
  width: 175px;
  padding: 10px;
  background-color: yellow;
  color: #333;
  border: none;
  border-radius: 5px;
}

.green {
  width: 175px;
  padding: 10px;
  background-color: green;
  color: white;
  border: none;
  border-radius: 5px;
  }
</style>
