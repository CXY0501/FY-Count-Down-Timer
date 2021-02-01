<template>
  <div class="home">
  <div class="middle">
    <div class="Month">
     <div class="title">TILL MONTH END</div>
     <div class="timer">
       <span>
         <div class="card">10</div>
       </span>
       <span>
         <div class="card">10</div>
       </span>
       <span>
         <div class="card">10</div>
       </span>
       <span>
         <div class="card">10</div>
       </span>
     </div>
     <div class="unit">
       <span>DAYS</span>
       <span>HOURS</span>
       <span>MINUTES</span>
       <span>SECONDS</span>
     </div>
    </div>
    <div class="Quarter">
     <div class="title">TILL QUARTER END</div>
     <div class="timer">
       <span>
         <div class="card">10</div>
       </span>
       <span>
         <div class="card">10</div>
       </span>
       <span>
         <div class="card">10</div>
       </span>
       <span>
         <div class="card">10</div>
       </span>
     </div>
     <div class="unit">
       <span>DAYS</span>
       <span>HOURS</span>
       <span>MINUTES</span>
       <span>SECONDS</span>
     </div>
    </div>
    <div class="Year">
     <div class="title">TILL YEAR END</div>
     <div class="timer">
       <span>
         <div class="card">10</div>
       </span>
       <span>
         <div class="card">10</div>
       </span>
       <span>
         <div class="card">10</div>
       </span>
       <span>
         <div class="card">10</div>
       </span>
     </div>
     <div class="unit">
       <span>DAYS</span>
       <span>HOURS</span>
       <span>MINUTES</span>
       <span>SECONDS</span>
     </div>
    </div>
  </div>
  <footer @click="configclick">
    Configuration
  </footer>
  </div>
  
</template>

<script>
// @ is an alias to /src

// Vue.component(VueCountdown.name, VueCountdown);

export default {
  name: 'Home',
  components: {
    
  },
  props:{
    path: String
  },
  methods:{
    configclick(){
      this.$router.replace(this.path)
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
  margin-left: 0.5vw;
  margin-right: 0.5vw;
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
footer{
  color: aliceblue;
  position: absolute;
  right:3vw;

}
</style>
