<template>
  <div class="Config">
    <h1>This is an config page</h1>
    <div class="backhome" @click="homeclick">
     Home
  </div>
  </div>
</template>

<script>
// @ is an alias to /src

// Vue.component(VueCountdown.name, VueCountdown);

export default {
  name: 'Config',
  components: {
    
  },
  props:{
    path: String
  },
  methods:{
    homeclick(){
      this.$router.replace('./')
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

</style>