<script>
import { RouterLink, RouterView } from 'vue-router'

</script>

<template>
  <h1>Bet Simulator</h1>
  <div class="Routes">
    <RouterLink to="/youtube"> go to youtube</RouterLink>
    <RouterLink to="/highLow"> go to Home</RouterLink>
    <RouterView />
  </div>

</template> 

<style scoped>
* {
  margin: auto;

}

h1 {
  text-align: center;

}

.Routes {
  text-align: center;
}
</style>
