<script>
export default {
  data() {
    return {
      myNumber: 0,
      enemyNumber: "?",
      gachaColor: "rgb(229, 69, 111)",
      updating: false,
      coin: 100,
      betInput: "",
      betStore: [],
      winOdds: "",
      drawOdds: "",
      loseOdds: "",
      winPercent: "",
      drawPercent: "",
      losePercent: "",
      radioValue: "",
      isSelected: false
    }
  },
  methods: {
    getRandom: function () {
      return Math.floor(Math.random() * 100);
    },
    slotMachine: function () {
      this.updating = true;
      this.gachaColor = "rgb(255, 156, 156)";
      const count = setInterval(() => {
        this.enemyNumber = this.getRandom();
      }, 100);
      setTimeout(() => {
        clearInterval(count);
        this.updating = false;
        this.gachaColor = "rgb(229, 69, 111)"
      }, 2000);
    }
  },
  created() {
    this.myNumber = this.getRandom();
  }
}
</script>

<template>

  <div id="box"> 
    <section id="infoBox">
      <div class="infoText">어느쪽이 이길까요?</div>

    </section>
    <section id="numBox">
      <div class="numCard" id="myNum">{{ myNumber }}</div>
      <div id="vs">vs</div>
      <div class="numCard" id="enemyNum" :style="{ backgroundColor : gachaColor }"> {{ enemyNumber }} </div>
    </section>
    <section>
      <div class="betSelecter">
        <input class="winRadio betSelect" name="betRadio" id="win" type="radio" v-model="radioValue" value="win"/>
        <label for="win" class="winLabel betLabel">승리</label>

        <input class="drawRadio betSelect" name="betRadio" id="draw" type="radio" v-model="radioValue" value="draw"/>
        <label for="draw" class="drawLabel betLabel">무승부</label>

        <input class="loseRadio betSelect" name="betRadio" id="lose" type="radio" v-model="radioValue" value="lose"/>
        <label for="lose" class="loseLabel betLabel">패배</label>
      </div>
    </section>
    
    
    <section id="betBox">
      <input id="betInput" v-model="betInput" placeholder="베팅 금액" />
      <button id="gacha" @click="slotMachine" :disabled="updating">BET</button>
      <div id="balance">보유 코인 : {{ coin }} </div>
    </section>

  </div>
</template>

<style scoped>
.betSelect {
  appearance: none;
  margin: 0;
}
.betLabel {
  flex:auto;
  height: 5rem;
}

.winLabel{
  background-color: rgb(64, 87, 217);
}
.drawLabel {
  background-color: rgb(124, 161, 64);
}
.loseLabel{
  background-color: rgb(229, 69, 111);
}

.winRadio:checked ~ .winLabel {
  filter: brightness(1.6);
}
.drawRadio:checked ~ .drawLabel {
  filter: brightness(1.6);
}
.loseRadio:checked ~ .loseLabel {
  filter: brightness(1.6);
}
.betSelecter{
  position: relative;
  top:28rem;
  display:flex; 
  flex-wrap: wrap;
  width: 100%;
  line-height: 3rem;

}

.labelBet {
  flex: auto;
  background-color: rgb(60, 76, 90);
  height: 3rem;
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
.infoText{
  position:absolute;
  top: 5%;
  left: 50%;
  transform: translate(-50%, -50%);
  font-size: large;
  color: white;
}
#numBox{
  display:flex; 
  flex-wrap: wrap;
  position: absolute;
  top: 10rem;
  left: 50%;
  transform: translate(-50%, -50%);
}
.numCard {
  width: 10rem;
  height: 10rem;
  line-height: 9.5rem;
  left: 10%;
  top: 10%;
  color: white;
  background-color: rgb(64, 87, 217);
  font-size: 6rem;
  border-radius: 1rem;
}
#vs {
  width: 10rem;
  line-height: 9rem;
  font-size: 4rem;
}
#box {
  width: 60rem;
  height: 40rem; 
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
  text-align: center;
  border-radius: 1rem;
  background-image: linear-gradient(rgb(128, 128, 128),rgb(128, 128, 128));
}



</style>