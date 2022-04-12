<template>
  <div class="canvas">
    <div
      @click="onClick"
      id="bulb"
      :class="clicks >= necessaryClicks ? 'bulb-on' : 'bulb-off'"
    >
      <div class="necesaryClickNumber">{{ necessaryClicks }}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "LigthBulb",
  data() {
    return {
      clicks: 0,
    };
  },
  props: ["necessaryClicks"],
  emit: ["switchedOn"],
  methods: {
    onClick() {
      this.clicks++;

      if (this.clicks == this.necessaryClicks) {
        this.$emit("switchedOn", 1);
      }

      if (this.clicks > this.necessaryClicks) {
        this.$emit("switchedOn", -1);
        this.clicks = 0;
      }

    },
  },
};
</script>

<style scoped>
.canvas {
  cursor: pointer;
  height: 500px;
  margin: 50px auto;
  text-align: center;
  box-sizing: border-box;
}

.bulb-off {
  width: 265px;
  height: 400px;
  background: url("lightoff.png") no-repeat;
  margin: auto;
}

.bulb-on {
  width: 265px;
  height: 400px;
  background: url("lighton.png") no-repeat;
  margin: auto;
}
.necesaryClickNumber {
  font-size: 5em;
  font-weight: 500;
  padding-top: 1em;
  user-select: none;
}
</style>