<template>
  <div class="betSelecter">
    <input class="winRadio betRadio" id="win" type="radio" v-model="radioValue" value="win" @click="radioIs"/>
    <label for="win" class="winLabel betLabel">승리</label>

    <input class="drawRadio betRadio" id="draw" type="radio" v-model="radioValue" value="draw" @click="radioIs"/>
    <label for="draw" class="drawLabel betLabel">무승부</label>

    <input class="loseRadio betRadio" id="lose" type="radio" v-model="radioValue" value="lose" @click="radioIs"/>
    <label for="lose" class="loseLabel betLabel">패배</label>
  </div>
</template>

<script>
export default {
  data() {
    return {
      radioValue : "",
      
    }
  },
  methods: {
    radioIs() {
      setTimeout(() => {
        this.$emit("radioIs", this.radioValue)
      }, 0);
    }
  }
  
}
</script>

<style scoped>
.betRadio {
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
</style>