<script>

</script>

<template>

  <div id="box">
    <div id="mybox">my</div>
    <div id="vs">VS</div>
    <div id="enemy">enemy</div>
    <div id="bill">bill</div>
  </div>
  

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
}
#mybox {
  display: inline-block;
  width: 20rem;
  height: 15rem;
  text-align: center;
  line-height: 15rem;
  background-color: darkslateblue;
  border-radius: 1rem;
  border: thick double #32a1ce;
  position: relative;
  top: 4rem;
  right: 8rem;
}
#vs{
  display: inline-block;
  margin: auto;
  position: relative;
  top: 4rem;
  text-align: center;
  line-height: 3rem;
  width: 3rem;
  height: 3rem;
  background-color: rgb(33, 33, 33);
  border-radius: 0.5rem;
}
#enemy{
  display: inline-block;
  width: 20rem;
  height: 15rem;
  text-align: center;
  line-height: 15rem;
  background-color: rgb(116, 66, 103);
  border-radius: 1rem;
  border: thick double #672b2b;
  position: relative;
  top: 4rem;
  left: 8rem;
  
}
#bill{
  position: relative;
  top: 15rem;
  width: 45rem;
  height: 15rem;
  margin: auto;
  background-color: rgb(46, 46, 46);
  line-height:15rem;border-radius: 1rem;
}

</style>