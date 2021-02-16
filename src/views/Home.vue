<template>
  <div class="home">

  <div class="middle">
    <div class="today">
      <div class="Ttitle">Now is {{nowTime}} on {{nowDate}}</div>
    </div>
    <div class="Month">
     <div class="title">TILL THIS MONTH END</div>
     <div class="timer">
         <div class="card1">
           <count-down v-on:start_callback="countDownS_cb(1)" v-on:end_callback="countDownE_cb(1)" 
            :dayTxt="' DAYS '" :hourTxt="' HOURS '" :minutesTxt="' MINUTES '" :secondsTxt="' SECONDS'"           
             :startTime="startTime" :endTime="endTime1"></count-down>
         </div>
     </div>
     <!-- <div class="unit">
       <span>DAYS</span>
       <span>HOURS</span>
       <span>MINUTES</span>
       <span>SECONDS</span>
     </div> -->
    </div>
    <div class="Quarter">
     <div class="title">TILL THIS QUARTER END</div>
     <div class="timer">
       <div class="card1">
         <count-down v-on:start_callback="countDownS_cb(1)" v-on:end_callback="countDownE_cb(1)" 
            :dayTxt="' DAYS '" :hourTxt="' HOURS '" :minutesTxt="' MINUTES '" :secondsTxt="' SECONDS'"         
             :startTime="startTime" :endTime="endTime2"></count-down>
       </div>
     </div>
     <!-- <div class="unit">
       <span>DAYS</span>
       <span>HOURS</span>
       <span>MINUTES</span>
       <span>SECONDS</span>
     </div> -->
    </div>
    <div class="Year">
     <div class="title">TILL THIS FISCAL YEAR END</div>
     <div class="timer">
       <div class="card1">
           <count-down v-on:start_callback="countDownS_cb(1)" v-on:end_callback="countDownE_cb(1)" 
            :dayTxt="' DAYS '" :hourTxt="' HOURS '" :minutesTxt="' MINUTES '" :secondsTxt="' SECONDS'"           
             :startTime="startTime" :endTime="endTime3"></count-down>
       </div>
     </div>
     <!-- <div class="unit">
       <span>DAYS</span>
       <span>HOURS</span>
       <span>MINUTES</span>
       <span>SECONDS</span>
     </div> -->
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
      endTime1: (new Date('2021-03-01 00:00:00')).getTime(),
      NextMonth: (new Date()).getMonth()+2,
      // NextMonthFirstDay: '2021-'+'0'+NextMonth+' 00:00:00',
      // endTime1: (new Date(NextMonthFirstDay)).getTime(),
      endTime2: (new Date('2021-04-01 00:00:00')).getTime(),
      endTime3: (new Date('2021-07-01 00:00:00')).getTime(),
      // NextMonth: '2021-03-01',
      currentTime:new Date(),
      timer:"",
      nowDate:null,    //存放年月日变量
      nowTime:null,   //存放时分秒变量
    }
  },
  created(){
    this.timer = setInterval(this.getTime, 1000);
  },
  props:{
    path: String
  },

  methods:{
    countDownS_sb(x){
      // console.log(x)
    },
    countDownS_cb(x){
      // console.log(x)
    },
    configclick(){
      this.$router.replace('./config')
    },
    getTime(){
      const date = new Date();
      const year = date.getFullYear();
      const month = date.getMonth() + 1;
      const day = date.getDate();
      const hour= date.getHours();
      const minute = date.getMinutes();
      const second = date.getSeconds();
      const str = ''
      // if(this.hour>12) {
      //   this.hour -= 12;
      //   this.str = " AM";
      //   }else{
      //   this.str = " PM";                        
      //   }
      this.month=check(month);
      this.day=check(day);
      this.hour=check(hour);
      this.minute=check(minute);
      this.second=check(second);
      function check(i){
        const num = (i<10)?("0"+i) : i;
        return num;
      }
      this.nowDate = this.month + "/" + this.day+"/" + year +" " ;
      this.nowTime = this.hour + ":" + this.minute;
      },
      // change(){
      //   this.endTime1 = (new Date(this.NextMonth+' 00:00:00')).getTime()
      // }
  },
  mounted(){
     this.$bus.$on('nextMonth',(data)=>{
        this.NextMonth = data
        this.endTime1 = (new Date(this.NextMonth+' 00:00:00')).getTime()
        this.CountDown.end = this.endTime1
      console.log(this.NextMonth)
    })
  },
  watch:{
    change(){
      this.today = new Date()
    }
  },
  beforeDestroy(){
     if (this.timer) {
      clearInterval(this.timer); // 在Vue实例销毁前，清除定时器
    }
  },
}
</script>

<style scoped>
.middle{
  position: fixed;
  margin-top: 25vh;
  margin-left: 12.5vw;
  width: 75vw;
  /* height: 20vh; */
}
.Month,.Quarter,.Year{
  /* display: inline-block; */
  /* width: 25vw; */
  text-align: center;
  font-size: 1.7vw;
  color: red;
}
.title{
  margin-left: 5vw;
  margin-bottom: -6vh;
  /* width: 20vw; */
  border-radius: 10px;
  font-weight:bold;
  /* background-color: black; */
  background: rgba(0, 0, 0, .9);
  color: white
}
.Ttitle{
  margin-left: 5vw;
  margin-bottom: 2vh;
  /* width: 20vw; */
  border-radius: 10px;
  font-weight:bold;
  /* background-color: black; */
  background: rgba(0, 0, 0, .9);
  color: red;
  text-align: center;
  font-size: 2vw;
}
.timer{
  margin-left: 5vw;
  /* margin-top: -1vh; */
  /* width: 20vw; */
  /* height: 5vh; */
  /* background-color: black; */
  background: rgba(0, 0, 0, .8)
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
  /* width: 20vw; */
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
  font-size: 3vw;
  font-weight: bolder;
  font-style: normal;
}

</style>
