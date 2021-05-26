<template>
  <div>
    <b-form-select v-model="selected" :options="selectArray" @change="handleSelectChanged(selected)" />
    <b-card-group>
      <b-card v-for="description in eventDescriptionsArray" :key="description.title" no-body>
        <b-card-header v-b-toggle="'accordion-' + description.id">
          {{ description.title }}
        </b-card-header>
        <b-collapse :id="'accordion-' + description.id">
          <b-list-group flush>
            <b-list-group-item v-for="option in description.options" :key="option.name">
              <div>{{ option.name }}</div>
              <div>{{ option.effect }}</div>
            </b-list-group-item>
          </b-list-group>
        </b-collapse>
      </b-card>
    </b-card-group>
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
