<template>
  <div>
    <b-form-select v-model="selected" :options="selectArray" @change="handleSelectChanged(selected)" />
    <b-list-group>
      <b-list-group-item v-for="description in eventDescriptionsArray" :key="description.title">
        <div>{{ description.title }}</div>
        <b-list-group>
          <b-list-group-item v-for="option in description.options" :key="option.name">
            <div>{{ option.name }}</div>
            <div>{{ option.effect }}</div>
          </b-list-group-item>
        </b-list-group>
      </b-list-group-item>
    </b-list-group>
  </div>
</template>

<script>
export default {
  props: {
    selectArray: {
      type: Array,
      default: null
    },
    eventArray: {
      type: Array,
      default: null
    }
  },
  data () {
    return {
      selected: null,
      eventDescriptionsArray: []
    }
  },
  methods: {
    handleSelectChanged (selected) {
      this.eventDescriptionsArray = this.eventArray.find(function (event) {
        return event.id === selected
      }).descriptions
    }
  }
}
</script>

<style></style>
