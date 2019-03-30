<template>
  <div class="input-group mb-3">
    <div class="input-group-prepend">
      <button class="btn btn-outline-danger" type="button" id="button-addon1" @click="mutableValue--">-</button>
    </div>
    <input type="number" class="form-control" placeholder="" aria-label="Example text with button addon"
           aria-describedby="button-addon1" :tabindex="tabindex" v-model="mutableValue" :min="min" :max="max">
    <div class="input-group-append">
      <button class="btn btn-outline-danger" type="button" id="button-addon2" @click="mutableValue++">+</button>
    </div>
  </div>
</template>

<script>
  export default {
    name: "InputNumber",
    props: {
      value: {type: Number},
      min: {type: Number},
      max: {type: Number},
      tabindex: {type: String, default: "0"},
    },
    data: function () {
      return {mutableValue: this.value}
    },
    watch: {
      mutableValue: function (newValue) {
        if (newValue < this.min) {
          this.mutableValue = this.min
        } else if (newValue > this.max) {
          this.mutableValue = this.max
        } else {
          this.$emit("input", newValue)
        }
      },
    },
  }
</script>
