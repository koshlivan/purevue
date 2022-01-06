<template>
  <div class="cap">
    <h3>Contacts</h3>
    <div>
      <button type="button" id="delContact" @click="deleteSelected"><span class="material-icons">remove_circle</span> Remove Selected</button>
      <button type="button" id="addContact" @click="showDialog"><span class="material-icons">add_circle</span> Add Contact</button>
    </div>
  </div>

</template>

<script>
export default {
  name: "Cap",
  emits:[
    'showModal',
    'deleteSelected'
  ],
  methods:{
    showDialog(){
      this.$emit('showModal');
    },
    deleteSelected(){
      this.$emit('deleteSelected');
    }
  }
}
</script>

<style scoped>

</style>