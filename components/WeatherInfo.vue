<template>
  <div>
    <h3>{{ cityName}}</h3>
    <p>Temperature:<strong>{{ currentTemp }}</strong></p>
    <p>
      <span v-if="hasMinTemp">min:<strong>{{ minTemp }}</strong></span>
      <span>max:
        <strong v-if="maxTemp !== ''">{{ maxTemp }}</strong>
        <strong v-else> -- </strong>
      </span>
    </p>
  </div>
</template>

<script>
export default {
  name: 'WeatherInfo',
  props: {
    cityName: {
      type: String,
      required: true
    },
    currentTemp: {
      type: Number,
      required: true
    },
    minTemp: {
      //way one
      type: [Number, String],
      default: '--', //if we dont have answer
      validator: function (value) {
        if(typeof value !== Number) {
          return false;
        }
      }
    },
    maxTemp: {
      //way two
      type: [Number, String],
      default: '', //if we dont have answer
    }
  },
  computed: {
    hasMinTemp() {
      return typeof value === Number
    }
  }
}
</script>

<style>

</style>
