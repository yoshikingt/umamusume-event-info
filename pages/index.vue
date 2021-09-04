<template>
  <div>
    <b-tabs justified>
      <b-tab title="育成ウマ娘" active>
        <Event :select-array="trainingSelectArray" :event-array="trainingEventArray" />
      </b-tab>
      <b-tab title="サポート">
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

    this.trainingEventArray.forEach((event) => {
      if (event.descriptions != null) {
        event.descriptions.forEach((description) => {
          // アコーディオン用にランダムな文字列を生成（v-b-toggle が食えないので数値はダメ）
          description.id = Math.random().toString(32).substring(2)
        })
      }
    })
    this.supportEventArray.forEach((event) => {
      if (event.descriptions != null) {
        event.descriptions.forEach((description) => {
          // アコーディオン用にランダムな文字列を生成（v-b-toggle が食えないので数値はダメ）
          description.id = Math.random().toString(32).substring(2)
        })
      }
    })
  }
}
</script>

<style></style>
