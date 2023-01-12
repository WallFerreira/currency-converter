<template>
  <div id="app">
    <h1 class="text-center">Conversor de moedas</h1>
    <div class="linha">
      <Conversor moeda-a="USD" moeda-b="BRL" />
      <Conversor moeda-a="BRL" moeda-b="USD" />
    </div>
    <div class="linha">
      <Conversor moeda-a="EUR" moeda-b="BRL" />
      <Conversor moeda-a="BRL" moeda-b="EUR" />
    </div>
    <div class="linha">
      <Conversor moeda-a="JPY" moeda-b="BRL" />
      <Conversor moeda-a="BRL" moeda-b="JPY" />
    </div>
  </div>
</template>

<script>
import Conversor from "./components/Conversor.vue";

export default {
  name: 'App',
  components: {
    Conversor,
  }
};
</script>

<style>
#app {
  margin: auto;
  max-width: 50rem;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  background-color:rgb(242, 233, 233) ;
}

.linha{
  margin-top: 40px;
  display: flex;
  justify-content: space-around;
}

.text-center{
  text-align: center;
}
</style>
