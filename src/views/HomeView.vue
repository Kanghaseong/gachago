<template>
  <section id="display"> 

    <div class="infoText">어느쪽이 이길까요?</div>

    <section id="numCards">
      <div :class="numCard"> {{ myNumber }} </div>
      <div id="vs">vs</div>
      <div :class="numCard" :style=" { backgroundColor : gachaColor } "> {{ enemyNumber }} </div>
    </section>

      <betSelecter @radioIs ="log"/>
      <betBox @enemyNumberIs="n => this.enemyNumber = n"
              @myNumberIs="n => this.myNumber = n"
      />

  </section>
</template>
<script>
import betSelecter from '../component/betSelecter.vue';
import betBox from '../component/betBox.vue';

export default {

  created() {
    this.myNumber = this.getRandom();
  },
  components: {
    betSelecter,
    betBox
  },

  data() {
    return {
      myNumber: 0,
      enemyNumber: "?",
      betStore: [],
      winOdd: "",
      drawOdd: "",
      loseOdd: "",
      gachaColor: "#e5456f",
      numCard:"numCard"
    }
  },
  methods: {
    log(e) {
      console.log(e)
    },
    getRandom: function () {
      return Math.floor(Math.random() * 100);
    },
    flash() {
      this.numCard = "numCardFlash";
      setTimeout(() => {
        this.numCard = "numCard";
      }, 500);

    },
    setGachaColor() {
      if (this.gachaColor === "#e5456f") {
        this.gachaColor = "#ff9c9c";
      } else {
        this.gachaColor = "#e5456f"
      }
    }
  },

}
</script>

<style scoped>
.numCardFlash {
  width: 10rem;
  height: 10rem;
  line-height: 9.5rem;
  left: 10%;
  top: 10%;
  color: white;
  background-color: rgb(64, 87, 217);
  font-size: 6rem;
  border-radius: 1rem;
  filter: brightness(30%);
}
.infoText{
  position:absolute;
  top: 5%;
  left: 50%;
  transform: translate(-50%, -50%);
  font-size: large;
  color: white;
}
#numCards{
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
#display {
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