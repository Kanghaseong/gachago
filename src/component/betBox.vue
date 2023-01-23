<template>
    <div id="betBox">
      <input id="betInput" v-model="betInput" placeholder="베팅 금액" />
      <button id="gacha" @click="slotMachine" :disabled="updating">BET</button>
      <div id="balance">보유 코인 : {{ coin }} </div>
    </div>
</template>

<script>
export default {
  props: {
    radioValue: String,
    myNumber: Number,
    enemyNumber: [Number, String]
  },

  data() {
    return {
      coin: 100,
      betInput: "",
      updating: false,
      myNum: this.myNumber,
      enemyNum: this.enemyNumber,
      gameScore: null,
    }
  },

  methods: {
    getRandom () {
      return Math.floor(Math.random() * 100);
    },
    enemyNumberIs() {
      this.$emit("enemyNumberIs", this.enemyNum);
    },
    myNumberIs() {
      this.$emit("myNumberIs", this.myNum);
    },
    setUpdating() {
      setTimeout(() => {
        this.updating = false;
      }, 1500);
    },

    slotMachine() {
      if (this.radioValue === "none") return alert("Select Bet type");

      this.updating = true;
      this.$parent.setGachaColor();

      const count = setInterval(() => {
        this.enemyNum = this.getRandom();
        this.enemyNumberIs();
      }, 100);
      setTimeout(() => {
        clearInterval(count);
      }, 1950);
      
      setTimeout(() => {
        this.$parent.setGachaColor();
        this.setGameScore();
        this.getGameResult();
        this.resetNumber();
        
      }, 2000); 
    },

    resetNumber() {
      setTimeout(() => {
        this.myNum = this.getRandom();
        this.enemyNum = "?";
        this.enemyNumberIs();
        this.myNumberIs();
        this.$parent.flash()
        this.setUpdating();
      }, 2000);
    },

    setGameScore() {
      this.gameScore = this.myNum - this.enemyNum;
    },
    getGameResult() {
      if (this.radioValue === "win" && this.gameScore > 0) {
        alert("Winner!")
      }
      else if (this.radioValue === "draw" && this.gameScore === 0) {
        alert("Winner!!")
      }
      else if (this.radioValue === "lose" && this.gameScore < 0) {
        alert("Winner!!!")
      }
      else {
        alert("you lose...")
      }
    },
    setSlip() {
      console.log(`my : ${this.myNum}, eme : ${this.enemyNum}, radio: ${this.radioValue}, gameScore : ${this.gameScore}`)
    }
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
  border-radius: 0.5rem;
  border: 0;
  font-size: 1rem;
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