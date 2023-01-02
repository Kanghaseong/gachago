<script>
export default {
  data() {
    return {
      myNumber: 0,
      enemyNumber: "?",
      gachaColor: "rgb(229, 69, 111)",
      updating: false
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
      <div class="numCard" id="enemyNum" :style="{backgroundColor : gachaColor}">{{ enemyNumber }}</div>
    </section>

    <section id="betBox">
      <div class="bet"></div>
      <div class="bet"></div>
      <div class="bet"></div>
    </section>

    <button id="gacha" @click="slotMachine" :disabled="updating">BET</button>

  </div>
</template>

<style scoped>

#gacha {
  position: absolute;
  top: 94%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 5rem;
  height: 2rem;

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
  border-radius: 2rem;
  background-image: linear-gradient(rgb(83, 83, 83),rgb(128, 128, 128));
}

#betBox {
  position: relative;
  top:28rem;
  display:flex; 
  flex-wrap: wrap;
  width: 100%;
}
.bet {
  display: inline-block;
  flex: auto;
  height: 7rem;
  line-height: 7rem;
}
.bet:nth-child(1){
  background-color: rgb(64, 87, 217);
}
.bet:nth-child(2){
  background-color: rgb(124, 161, 64);
}
.bet:nth-child(3){
  background-color: rgb(229, 69, 111);
}



</style>