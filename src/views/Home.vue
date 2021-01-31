<template>
  <div class="home">
  <div class="middle">
    <span class="Month">
     <div>Till Month End</div>
    </span>
    <span class="Quarter">
     <div>Till Quarter End</div>
    </span>
    <span class="Year">
     <div>Till Year End</div>
    </span>
  </div>
  </div>
</template>

<script>
// @ is an alias to /src


export default {
  name: 'Home',
  components: {
    
  }
}
</script>

<style scoped>
.middle{
  position: fixed;
  margin-top: 40vh;
  margin-left: 12.5vw;
  width: 75vw;
  height: 20vh;
}
.middle span{
  display: inline-block;
  width: 25vw;
  text-align: center;
  color: red;
}
.middle div{
  margin-left: 5vw;
  width: 15vw;
  border-radius: 10px;
  background-color: black;
}

</style>
