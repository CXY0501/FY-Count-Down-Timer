<template>
  <div class="home">
  <div class="middle">
    <div class="Month">
     <div class="title">MONTH END</div>
     <div class="timer">
         <div class="card1">
           <count-down v-on:start_callback="countDownS_cb(1)" v-on:end_callback="countDownE_cb(1)" 
            :dayTxt="'   '" :hourTxt="'   '" :minutesTxt="'   '" :secondsTxt="'  '"           
             :startTime="startTime" :endTime="endTime1"></count-down>
         </div>
     </div>
     <div class="unit">
       <span>DAYS</span>
       <span>HOURS</span>
       <span>MINUTES</span>
       <span>SECONDS</span>
     </div>
    </div>
    <div class="Quarter">
     <div class="title">QUARTER END</div>
     <div class="timer">
       <div class="card1">
         <count-down v-on:start_callback="countDownS_cb(1)" v-on:end_callback="countDownE_cb(1)" 
            :dayTxt="'   '" :hourTxt="'   '" :minutesTxt="'   '" :secondsTxt="'  '"           
             :startTime="startTime" :endTime="endTime2"></count-down>
       </div>
     </div>
     <div class="unit">
       <span>DAYS</span>
       <span>HOURS</span>
       <span>MINUTES</span>
       <span>SECONDS</span>
     </div>
    </div>
    <div class="Year">
     <div class="title">FISCAL YEAR END</div>
     <div class="timer">
       <div class="card1">
           <count-down v-on:start_callback="countDownS_cb(1)" v-on:end_callback="countDownE_cb(1)" 
            :dayTxt="'   '" :hourTxt="'   '" :minutesTxt="'   '" :secondsTxt="'  '"           
             :startTime="startTime" :endTime="endTime3"></count-down>
       </div>
     </div>
     <div class="unit">
       <span>DAYS</span>
       <span>HOURS</span>
       <span>MINUTES</span>
       <span>SECONDS</span>
     </div>
    </div>
  </div>
  <div class="config" @click="configclick">
    Configuration
  </div>
  </div>
</template>

<script>
// @ is an alias to /src

// Vue.component(VueCountdown.name, VueCountdown);
import CountDown from 'vue2-countdown'

export default {
  name: 'Home',
  components: {
    CountDown
  },
  data(){
    return{
      startTime: (new Date()).getTime(),
      endTime1: 1614528000,
      endTime2: 1617206400,
      endTime3: 1625068800
    }
  },
  props:{
    path: String
  },
  methods:{
    countDownS_sb(x){
      console.log(x)
    },
    countDownS_cb(x){
      console.log(x)
    },
    configclick(){
      this.$router.replace('./config')
    }
  }
}
</script>

<style scoped>
.middle{
  position: fixed;
  margin-top: 25vh;
  margin-left: 12.5vw;
  width: 75vw;
  height: 20vh;
}
.Month,.Quarter,.Year{
  display: inline-block;
  width: 25vw;
  text-align: center;
  font-size: 1.7vw;
  color: red;
}
.title{
  margin-left: 5vw;
  margin-bottom: -7vh;
  width: 20vw;
  border-radius: 10px;
  font-weight:bold;
  /* background-color: black; */
  background: rgba(0, 0, 0, .8);
  color: rgb(243, 77, 77);
}
.timer{
  margin-left: 5vw;
  margin-top: -1vh;
  width: 20vw;
  height: 5vh;
  /* background-color: black; */
  background: rgba(0, 0, 0, .6)
}
.timer span{
  display: inline-block;
  width: 5vw;
  margin-top: 2vh;
  text-align: center;
  /* margin-left: 0.25vw;
  margin-right: 0.25vw; */
}
.unit{
  margin-left: 5vw;
  width: 20vw;
  height: 5vh;
  /* background-color: black; */
  background: rgba(0, 0, 0, .6);
  font-size: 0.8vw;
  color: rgb(243, 77, 77);
}
.unit span{
  display: inline-block;
  width: 4vw; 
  margin-top: 2vh;
  margin-left: 0.22vw;
  margin-right: 0.22vw;
  text-align: center;
  background: rgba(0, 0, 0, .6);
}
.card{
  height: 5vh;
  width: 3vw;
  line-height: 5vh;
  margin-left: 1vw;
  background-color: black;
}
.config{
  color: aliceblue;
  position: absolute;
  right:3vw;
  cursor: pointer;
}
.number{
  color: aliceblue;
}
.card1{
  font-size: 3.2vw;
  font-weight: bolder;
}

</style>
