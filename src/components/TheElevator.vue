<template>
  <div class="elevator" :style="{ top: elevatorPosition + 'px' }">Elevator</div>
</template>

<script>
export default {
  props: ['currentFloor'],
  data() {
    return {
      elevatorPosition: 0
    }
  },
  watch: {
    currentFloor(newFloor) {
      this.moveElevatorTo(newFloor);
    }
  },
  methods: {
    moveElevatorTo(floor) {
      const floorHeight = 138; // Height of each floor in pixels
      const targetPosition = (floor -1) * floorHeight;
      
      // Smoothly move the elevator to the target position
      const animationDuration = Math.abs(this.elevatorPosition - targetPosition) * 5; // Adjust speed based on distance
      this.elevatorPosition = targetPosition;
      
      setTimeout(() => {
        this.$emit('arrive', floor);
      }, animationDuration);
    }
  }
};
</script>

<style scoped>
.elevator {
  margin-top: 60px;
  margin-left: 60px;
  width: 100px;
  height: 140px;
  background-color: #333;
  color: #fff;
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 5px;
  position: absolute;
  transition: top 1.5s;
}
</style>
