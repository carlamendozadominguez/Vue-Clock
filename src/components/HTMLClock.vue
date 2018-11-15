<template>
  <div class= "html-clock">
    <div class = "hour">{{ hours }}</div>
    <div class = "sep"> : </div>
    <div class="minutes">{{ minutes }}</div>
    <div class="sep"> : </div>
    <div class="seconds">{{ seconds }}</div>
</template>

<style lang = "postcss" scoped>
  .html-clock {
    display: grid;
    grid-template-columns: 3fr 1fr 3fr 1fr 3fr 1.5fr;
    justify-content: center;
    align-items: center;
    width: 500px;
    height: 125px;
    font-size: 50px;
  }

  .html-clock > div {
    display: flex;
    justify-content: center;
  }

  .sep {
    animation: papasitoBlink 1s linear infinite;
  }
  
  @keyframes papasitoBlink {
    0%,
    49% { opacity: 1; }
    
    50%,
    100% { opacity: 0; }
  }
  
  .red-lcd { color: red; }
  .green-lcd { color: green; }
  .yellow-lcd { color: yellow; }

</style>

<script>
export default {
  props: ['theme'],
  data (){
    return {
      hours: '--',
      minutes: '--',
      seconds: '--'
    }
  },
   created(){
     setInterval( () => this.updateTime(), 1000);
  },

  methods: {
    updateSeconds() {
      this.seconds = this.prettyTime(new Date().getSeconds());
    },

    updateMinutes() {
      this.minutes = this.prettyTime(new Date().getMinutes());
    },
    
    updateHours(){
      this.hours = this.prettyTime(new Date().getHours());
    },

    prettyTime(time){
      return String(time).padStart(2, "0");
    },

    updateTime(){
      this.updateSeconds();
      this.updateMinutes();
      this.updateHours();
    }
  },
  computed: {
  },
  watch: {
    
  },
}
</script>





