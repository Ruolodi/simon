<template>
  <div class="mainBlock">
    <div class="container">
      <button
        :class="cardNumber === 1 ? 'card active' : 'card'"
        :disabled="canPlay === false"
        @click="clickUser(1)"
      ></button>
      <button
        :class="cardNumber === 2 ? 'card1 active' : 'card1'"
        :disabled="canPlay === false"
        @click="clickUser(2)"
      ></button>
      <button
        :class="cardNumber === 3 ? 'card2 active' : 'card2'"
        :disabled="canPlay === false"
        @click="clickUser(3)"
      ></button>
      <button
        :class="cardNumber === 4 ? 'card3 active' : 'card3'"
        :disabled="canPlay === false"
        @click="clickUser(4)"
      ></button>
    </div>
    <button class="start" v-if="isStarting === false" @click="start">
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
      turn: 1,
      isStarting: false,
      canPlay: false,
      cardNumber: 0,
      isMistake: false,
    }
  },
  methods: {
    loopColors(counter = 0) {
      if (counter < this.arrComp.length) {
        //проверка на выход из метода

        this.flashing(counter)
      }
      this.canPlay = true
    },

    flashing(counter) {
      setTimeout(() => {
        this.cardNumber = this.arrComp[counter]
        console.log(this.cardNumber)
        setTimeout(() => {
          this.cardNumber = 0
          console.log(this.cardNumber)
          this.loopColors(++counter)
        }, 300)
      }, 300)
    },
    clickUser(id) {
      this.arrUser.push(id)
      this.isMistake =
        this.arrUser[this.arrUser.length - 1] !==
        this.arrComp[this.arrUser.length - 1] //Сравнение массивов
      if (this.isMistake) {
        this.isStarting = false
        this.arrUser.length = 0
        this.arrComp.length = 0
      } else if (this.arrUser.length === this.arrComp.length) {
        this.arrUser.length = 0
        this.start()
      }
      console.log("проверка", this.isMistake)

      /* let array1 = [4,8,9,10]
let array2 = [4,8,9,10]
let is_same = 
    (array1.length == array2.length) && 
    array1.every((val, i) => {
        return val === array2[i] 
}); */ //сокращенный вариант for

      console.log("user", this.arrUser)
    },
    start() {
      this.isStarting = true
      let numComp = Math.floor(Math.random() * (5 - 1) + 1)
      this.arrComp.push(numComp)
      this.loopColors()
    },
  },
}
</script>

<style></style>
