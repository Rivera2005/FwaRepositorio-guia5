<template>
  <div id="app">
    <CharacterList></CharacterList>
  </div>
</template>

<script>
import CharacterList from './components/CharacterList.vue';

export default {
  name: 'App',
  components: {
    CharacterList
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Creepster&display=swap');

body {
  margin: 0;
  padding: 0;
  font-family: Arial, sans-serif;
  background-color: #1a1a1a;
  color: #ffffff;
}

#app {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
}

.rick-and-morty-title {
  font-family: 'Creepster', cursive;
  text-align: center;
  font-size: 48px;
  margin-bottom: 30px;
  color: #00b5cc;
  text-shadow: 
      0 0 5px #fff,
      0 0 10px #fff,
      0 0 15px #fff,
      0 0 20px #00b5cc,
      0 0 35px #00b5cc,
      0 0 40px #00b5cc,
      0 0 50px #00b5cc,
      0 0 75px #00b5cc;
}

@media (max-width: 480px) {
  .rick-and-morty-title {
    font-size: 36px;
  }
}
</style>