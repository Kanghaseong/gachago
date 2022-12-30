<script>

</script>

<template>

  <div id="box">
    <div id="mybox">my</div>
    <div id="vs">VS</div>
    <div id="enemybox">enemy</div>

  </div>
  <div id="bill">bill</div>

</template>

<style scoped>

#box {
  width: 70rem;
  height: 50rem;
  text-align: center;
  margin: auto;
  margin-top: 4rem;
  background-color:rgb(54, 54, 54);
  border-radius: 2rem;

  display: flex;
  flex-direction: row;

}
#mybox, #vs, #enemybox {
  width: 25rem;
  height: 15rem;
}

#mybox {
  background-color: brown;
}
#vs{
  background-color: blueviolet;
}
#enemybox{
  background-color:chocolate
}

</style>