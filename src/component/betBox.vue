<template>
    <div id="betBox">
      <input id="betInput" v-model="betInput" placeholder="베팅 금액" />
      <button id="gacha" @click="slotMachine" :disabled="updating">BET</button>
      <div id="balance">보유 코인 : {{ coin }} </div>
    </div>
</template>

<script>
export default {
  
  data() {
    return {
      coin: 100,
      betInput: "",
      updating: false,
      
    }
  },

  methods: {
    getRandom () {
      return Math.floor(Math.random() * 100);
    },
    enemyNumberIs() {
      this.$emit("enemyNumberIs", this.enemyNumber);
    },
    myNumberIs() {
      this.$emit("myNumberIs", this.myNumber);
    },
    slotMachine () {
      this.updating = true;
      this.$parent.setGachaColor();

      const count = setInterval(() => {
        this.enemyNumberIs();
        this.enemyNumber = this.getRandom();
      }, 100);

      setTimeout(() => {
        clearInterval(count);
        this.updating = false;
        this.$parent.setGachaColor();
        this.resetNumber()
      }, 2000);
    },
    resetNumber() {
      setTimeout(() => {
        this.myNumber = this.getRandom();
        this.enemyNumber = "?";
        this.enemyNumberIs();
        this.myNumberIs();
        this.$parent.flash()
      }, 2000);
    },
  }
}
</script>

<style scoped>
#gacha {
  position: absolute;
  top: 94%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 5rem;
  height: 2rem;
  border-radius: 5rem;
  border: 0;
}
#gacha:hover {
  background-color: rgb(41, 159, 92);
}
#balance {
  position: absolute;
  background-color: rgb(179, 206, 178);
  top: 92%;
  left: 80%;
  padding: 2px;
  border-radius: 0.5rem;
}
#betInput{
  position:absolute;
  left: 5%;
  top: 92%;
  outline: none;
  height: 1.5rem;
  font-size: 15px;
  border: 0;
  border-radius: 15px;
  outline: none;
  padding-left: 10px;
  background-color: rgb(233, 233, 233);

}
#betInput:hover {
  background-color: azure;
}
</style>