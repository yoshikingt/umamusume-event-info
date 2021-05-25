<template>
  <div>
    <b-tabs justified>
      <b-tab title="育成ウマ娘" active>
        <Event :select-array="trainingSelectArray" :event-array="trainingEventArray" />
      </b-tab>
      <b-tab title="サポートカード">
        <Event :select-array="supportSelectArray" :event-array="supportEventArray" />
      </b-tab>
    </b-tabs>
  </div>
</template>

<script>
export default {
  data () {
    return {
      trainingSelectArray: [],
      trainingEventArray: [],
      supportSelectArray: [],
      supportEventArray: []
    }
  },
  mounted () {
    this.trainingSelectArray = require('@/assets/json/training/select.json')
    this.trainingEventArray = require('@/assets/json/training/event.json')
    this.supportSelectArray = require('@/assets/json/support/select.json')
    this.supportEventArray = require('@/assets/json/support/event.json')
  }
}
</script>

<style></style>
