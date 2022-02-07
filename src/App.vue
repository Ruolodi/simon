<template>
 <div class="mainBlock">
    <div class="container">
      <div class="card" @click="clickUser(1)"></div>
      <div class="card1" @click="clickUser(2)"></div>
      <div class="card2" @click="clickUser(3)"></div>
      <div class="card3" @click="clickUser(4)"></div>
    </div>
     <button class="start" @click="start">
      Start
      </button>
 </div>
  
  
 
</template>

<script>
export default {
  data() {
    return {
      arrComp: [],
      arrUser: [],
    }
  },
  methods: {
    clickUser(id){
      this.arrUser.push(id)
      console.log(this.arrUser)
    },
    start(){
      let num = getRandomInt(4)
      console.log(num)
    }
  },
}
</script>

<style></style>
