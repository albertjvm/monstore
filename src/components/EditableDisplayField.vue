<template>
  <div class="editable-display-field">
    <input v-if="editMode" type="text" v-on:blur="handleSave" ref="input" :value="value" />
    <span v-else v-on:click="handleEdit">{{value}}</span>
  </div>
</template>

<script>
export default {
  name: 'EditableDisplayField',
  props: ['value'],
  data () {
    return {
      editMode: false
    }
  },
  methods: {
    handleEdit () {
      this.toggleEditMode()
    },
    handleSave () {
      this.$emit('input', this.$refs.input.value)
      this.toggleEditMode()
    },
    toggleEditMode () {
      this.editMode = !this.editMode
    }
  }
}
</script>

<style lang="scss" scoped>
  .editable-display-field {
    span, input {

    }
    input {

    }
  }
</style>
