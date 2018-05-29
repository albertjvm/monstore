<template>
  <div class="monster">
    <EditableDisplayField v-model="monster.name" v-on:input="handleNameChange(monster.name)" />
  </div>
</template>

<script>
import firebase from 'firebase'
import EditableDisplayField from '@/components/EditableDisplayField'

export default {
  name: 'Monster',
  components: {
    'EditableDisplayField': EditableDisplayField
  },
  firebase () {
    return {
      monster: {
        source: firebase.database().ref('monsters').child(this.$route.params.id),
        asObject: true
      }
    }
  },
  methods: {
    handleNameChange (name) {
      this.$firebaseRefs.monster.child('name').set(name)
    }
  }
}
</script>

<style lang="scss" scoped>
  .monster {

  }
</style>
