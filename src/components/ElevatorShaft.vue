// ElevatorShaft.vue
<template>
  <div class="elevator-shaft">
    <TheElevator :currentFloor="elevator.currentFloor" />
    <TheFloor v-for="floor in totalFloors" :key="floor" :floorNumber="floor" :currentFloor="elevator.currentFloor" @callElevator="callElevator"/>
  </div>
</template>

<script>
import TheElevator from './TheElevator.vue';
import TheFloor from './TheFloor.vue';

export default {
  data() {
    return {
      totalFloors: 5,
      elevator: {
        currentFloor: 1,
        targetFloor: 1,
        queue: [],
        passengers: []
      }
    };
  },
  components: {
    TheElevator,
    TheFloor
  },
  methods: {
    callElevator(floorNumber) {
      if (floorNumber !== this.elevator.currentFloor) {
        this.elevator.queue.push(floorNumber);
        if (this.elevator.queue.length === 1) {
          this.moveElevator();
        }
      }
    },
    moveElevator() {
      const interval = setInterval(() => {
        if (this.elevator.currentFloor < this.elevator.targetFloor) {
          this.elevator.currentFloor++;
        } else if (this.elevator.currentFloor > this.elevator.targetFloor) {
          this.elevator.currentFloor--;
        } else {
          clearInterval(interval);
          this.handleArrival();
        }
      }, 1000);
    },
    handleArrival() {
      const nextFloor = this.elevator.queue.shift();
      this.elevator.targetFloor = nextFloor;

      // Check for passengers to pick up on the way down
      const passengersToPickUp = this.elevator.queue.filter(floor => floor < nextFloor);
      passengersToPickUp.forEach(passengerFloor => {
        this.elevator.passengers.push(passengerFloor);
        const index = this.elevator.queue.indexOf(passengerFloor);
        this.elevator.queue.splice(index, 1);
      });

      if (this.elevator.passengers.length > 0) {
        this.elevator.targetFloor = 1; // Take passengers to the first floor
        this.moveElevator();
      } else if (this.elevator.queue.length > 0) {
        this.moveElevator();
      }
    }
  }
};
</script>

<style scoped>

</style>
