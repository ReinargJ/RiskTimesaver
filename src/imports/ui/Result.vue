<template>
    <div class="result">
        <span class="text-att">{{value.attLosses}}</span> - <span class="text-def">{{value.defLosses}}</span>
        <details-fight :result="value"></details-fight>
    </div>

</template>

<<script>
import DetailsFight from './DetailsFight';

export default {
  props:{
      value: {
          type: Object,
          required: true,
      }
  },
  components: {
      DetailsFight
  }
}
</script>

<style lang="less" scoped>
    .result {
        width: fit-content;
        margin: auto;
    }
</style>

<style lang="less">
    .result:hover {
        .result-details {
            display: block;
        }
    }
</style>
