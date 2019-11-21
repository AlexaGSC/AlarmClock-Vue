<template>
  <div class="container">
    <div class="clock">
      <div class="hours">
        {{ hours | toHuman }}
      </div>
      <div class="minutes">
        {{ minutes | toHuman }}
      </div>
      <div class="seconds">
        {{ seconds | toHuman }}
      </div>
      <div class="mode">
        {{ mode | toHuman }}
      </div>
    </div>
  </div>
</template>

<script>

export default {

  name: 'HtmlClock',

  filters: {
    toHuman(value) {
      return value.toString().padStart(2, '0');
    }
  },

  data() {
    return {
      hours: '--',
      minutes: '--',
      seconds: '--',
      mode: '--'
    }
  },

  mounted() {
    setInterval(this.tick, 1000);
  },

  methods: {
    tick() {
      const date = new Date();
      this.hours = date.getHours();
      this.minutes = date.getMinutes();
      this.seconds = date.getSeconds();
      this.mode = this.hours >= 12 ? 'PM' : 'AM';
    }
  }
}
</script>

<style>
  :root {
    text-align: center;
  }

  @font-face {
    font-family: 'DS-Digital';
    src: url('../assets/DS-Digital.woff') formar ('woff2');
    font-weight: normal;
    font-style: normal;
  }

  .container {
    background: grey;
    height: 150px;
    width: 450px;
    margin: auto;
    display: flex;
    -ms-flex-align: center;
  }

  .clock {
    background: black;
    height: 100px;
    width: 380px;
    margin: auto;
    display: flex;
    justify-content: space-around;
  }

  .hours {
    height: 90px;
    width: 90px;
    color: rgb(61, 250, 61);
    display: flex;
    flex-direction: column;
    justify-content: center;
    -ms-flex-align: center;
    font-size: 30px;
    font-family: 'DS-Digital';
  }

  .minutes {
    height: 90px;
    width: 90px;
    color: rgb(61, 250, 61);
    display: flex;
    flex-direction: column;
    justify-content: center;
    -ms-flex-align: center;
    font-size: 30px;
    font-family: 'DS-Digital';
  }

  .seconds {
    height: 90px;
    width: 90px;
    color: rgb(61, 250, 61);
    display: flex;
    flex-direction: column;
    justify-content: center;
    font-size: 30px;
    font-family: 'DS-Digital';
  }

  .mode {
    height: 90px;
    width: 90px;
    color: rgb(61, 250, 61);
    display: flex;
    flex-direction: column;
    justify-content: center;
    -ms-flex-align: center;
    font-size: 30px;
    font-family: 'DS-Digital';
  }
</style>
