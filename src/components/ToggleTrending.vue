<script>
export default {
  methods: {
    switchTrending() {
      this.$emit("switchTrending");
    },
  },
};
</script>

<template>
  <label class="switch">
    <input type="checkbox" />
    <span @click="switchTrending" class="slider"></span>
  </label>
</template>

<style scoped>
.switch {
  position: relative;
  display: inline-block;
  width: 120px;
  height: 34px;
  margin-left: 10px;
}

.switch input {
  display: none;
}

.slider {
  position: absolute;
  cursor: pointer;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgba(var(--bg-dark-blue), 1);
  -webkit-transition: 0.4s;
  transition: 0.4s;
  border-radius: 34px;
}

.slider:before {
  position: absolute;
  content: "";
  height: 26px;
  width: 26px;
  left: 4px;
  bottom: 4px;
  background-color: white;
  -webkit-transition: 0.4s;
  transition: 0.4s;
  border-radius: 50%;
}

input:checked + .slider {
  background-color: rgba(var(--bg-light-blue), 1);
}

input:focus + .slider {
  -webkit-box-shadow: 0 0 1px #2196f3;
  box-shadow: 0 0 1px #2196f3;
}

input:checked + .slider:before {
  -webkit-transform: translateX(26px);
  -ms-transform: translateX(26px);
  transform: translateX(85px);
}

/*------ ADDED CSS ---------*/
.slider:after {
  content: "Today";
  color: white;
  display: block;
  position: absolute;
  -webkit-transform: translate(-50%, -50%);
  -ms-transform: translate(-50%, -50%);
  transform: translate(-50%, -50%);
  top: 50%;
  left: 50%;
  font-size: 10px;
  font-family: Verdana, sans-serif;
}

input:checked + .slider:after {
  content: "This Week";
}

/*--------- END --------*/
</style>
