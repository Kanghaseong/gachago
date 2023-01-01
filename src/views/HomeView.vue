<script>
export default {
  data() {
    return {
      myNumber: 0
      }
  },
  methods: {
    getRandom: function () {
      let num = Math.floor(Math.random() * 100);
      this.myNumber = num;
      return num
    }
  }
}
</script>

<template>
  <div id="box"> 
    <section id="infoBox">
      <div class="infoText">어느쪽이 이길까요?</div>

    </section>
    <section id="numBox">
      <div class="numCard" id="myNum">{{ getRandom() }}</div>
      <div id="vs">vs</div>
      <div class="numCard" id="enemyNum">70</div>
    </section>

    <section id="betBox">
      <div class="bet"></div>
      <div class="bet">2</div>
      <div class="bet">3</div>
    </section>

  </div>
</template>

<style scoped>
.infoText{
  position:absolute;
  top: 5%;
  left: 50%;
  transform: translate(-50%, -50%);
  
  font-size: large;
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
  background-color: aquamarine;
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
  flex: auto;
  height: 8rem;
  line-height: 8rem;
}
.bet:nth-child(1){
  background-color: rgb(28, 41, 107);
}
.bet:nth-child(2){
  background-color: rgb(106, 138, 54);
}
.bet:nth-child(3){
  background-color: rgb(198, 144, 56);
}



</style>