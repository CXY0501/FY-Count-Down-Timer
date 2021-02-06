<template>
  <div class="Config">
    <div class="backhome" @click="homeclick">
     Home
    </div>
    <div class="configtable">
    <table>
      <th>1st day of next month</th>
      <tr><input type="date" v-model="nextMonth"></tr>
       <th>1st day of next quarter</th>
      <tr><input type="date" v-model="nextQuarter"></tr>
       <th>1st day of next FY</th>
      <tr><input type="date" v-model="nextFY"></tr>
    </table>
    <button @click="submit">Submit</button>
    </div>

  </div>
</template>

<script>
// @ is an alias to /src

// Vue.component(VueCountdown.name, VueCountdown);

export default {
  name: 'Config',
  data(){
    return{
      nextMonth:'',
      nextQuarter:'',
      nextFY:''
    }
  },
  components: {
    
  },
  props:{
    path: String
  },
  methods:{
    homeclick(){
      this.$router.replace('./')
    },
    submit(){
      this.$bus.$emit('nextMonth',this.nextMonth)
      // console.log(this.nextMonth)
      // console.log(this.nextQuarter)
      // console.log(this.nextFY)
      // this.$router.push({
      //  path:'./'})
    }
  }
}
</script>

<style scoped>
.backhome{
  color: aliceblue;
  position: absolute;
  right:3vw;
  cursor: pointer;
}
.configtable{
  background: rgba(0, 0, 0, .6);
  width: 20vw;
  height: 30vh;
  position:fixed;
  left:70vw;
  /* top:10vh; */
  color:#fff
}
table{
  background: rgba(0, 0, 0, .6);
  margin-top: 2vh;
  margin-left: 3vw;
}
button{
  margin-top: 2vh;
  margin-left: 7vw;
}
</style>