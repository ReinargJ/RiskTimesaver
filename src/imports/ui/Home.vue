<template>
  <div class="home">
    <stats-panel class="content-box"></stats-panel>
    
    <div class="content-box">
      <fight-panel @fightEnd="handleFightEnd"></fight-panel>
      <results v-if="winner != ''" :winner="winner" :results="results"></results>
     </div>
  </div>
</template>

<script>
import FightPanel from './FightPanel.vue';
import StatsPanel from './StatsPanel.vue';
import Results from './Results';

export default {
  data() {
    return {
      results: [],
      winner: "",
    }
  },

  components: {
    FightPanel,
    StatsPanel,
    Results
  },

  methods: {
    handleFightEnd(winner, results){
      this.results = results;
      this.winner = winner
    }
  }
}
</script>

<style lang="less" scoped>
.home {
  text-align: center;
}
</style>

<style lang="less">
.text-att {
  &.important {
    font-weight: bold;
  }
  color: red;
}

.text-def {
  &.important {
    font-weight: bold;
  }
  color: blue;
}
</style>
