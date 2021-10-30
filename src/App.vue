<template>
  <div class="container">
    <Info-block 
    @timeframeChange="currentTimeframe = $event" 
    :currentTimeframe="currentTimeframe"/>
    <div class="cards">
        <Card 
        v-for="(cardData, index) in list" :key="index"
        :cardData="cardData" 
        :currentTimeframe="currentTimeframe" />
    </div>
  </div>
</template>

<script>
  import Card from '@/components/Card.vue'
  import InfoBlock from '@/components/InfoBlock.vue'
  import dataList from '@/assets/data/data.json'
export default {
  name: 'App',
  components: {
    InfoBlock,
    Card
  },
  data () {
    return {
      list: dataList,
      currentTimeframe : 'daily',
    }
  }
}
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Rubik:wght@300;400;500&display=swap');
@import '@/assets/variables.scss';
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: 'Rubik', sans-serif;
  background: $very-dark-blue;
  color: #fff;
  font-weight: 300;
}
#app {
  display: grid;
  place-items: center;
}
h3, a {
  font-size: 1.125rem;
}
p {
  color: $text-muted;
}
.container {
  max-width: 90%;
  margin: 5rem auto;
}
.cards {
  display: grid;
  grid-template-columns: 1fr;
  gap: 1.5rem;
  margin: 1.5rem 0;
}
@media (min-width: 50em) {
  .cards {
    grid-template-columns: repeat(2, minmax(250px, 1fr));
  }
}
@media (min-width: 70em) {
  #app {
    height: 100vh;
  }
  .container {
    max-width: 70rem;
    display: grid;
    grid-template-columns: 1fr 3fr;
    gap: 1.5rem;
  }
  .cards {
    grid-template-columns: repeat(3, minmax(230px, 1fr));
    margin: 0;
  }
}
</style>
