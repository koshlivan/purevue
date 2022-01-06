<template>
  <table>
    <tr>
      <th><input type="checkbox" name="selectAll" @change="$emit('setAllChecked')"></th>
      <th>
        <div>
          <h5>Preview</h5>
        </div>

      </th>
      <th>
        <div>
          <h5>Name</h5>
        </div>
        <div class="arrows">
          <span class="material-icons" @click="sortNameAsc">arrow_drop_up</span>
          <span class="material-icons" @click="sortNameDesc">arrow_drop_down</span>
        </div>
      </th>
      <th>
        <div>
          <h5>Email</h5>
        </div>
        <div class="arrows">
          <span class="material-icons" @click="sortEmailAsc">arrow_drop_up</span>
          <span class="material-icons" @click="sortEmailDesc">arrow_drop_down</span>
        </div>
      </th>
      <th>
        <div>
          <h5>Address</h5>
        </div>
        <div class="arrows">
          <span class="material-icons" @click="sortAddressAsc">arrow_drop_up</span>
          <span class="material-icons" @click="sortAddressDesc">arrow_drop_down</span>
        </div>
      </th>
      <th>
        <div>
          <h5>Created</h5>
        </div>
        <div class="arrows">
          <span class="material-icons" @click="sortCreatedAsc">arrow_drop_up</span>
          <span class="material-icons" @click="sortCreatedDesc">arrow_drop_down</span>
        </div>
      </th>
      <th></th>
    </tr>
  </table>
</template>

<script>
export default {
  name: "TableHead",
  emits:[
    'setAllChecked',
    'sortNameAsc',
    'sortEmailAsc',
    'sortEmailDesc',
    'sortAddressAsc',
    'sortAddressDesc',
    'sortCreatedAsc',
    'sortCreatedDesc'
  ],
  methods:{
    sortNameAsc(){
      this.$emit('sortNameAsc')
    },
    sortNameDesc(){
      this.$emit('sortNameDesc')
    },
    sortEmailAsc(){
      this.$emit('sortEmailAsc')
    },
    sortEmailDesc(){
      this.$emit('sortEmailDesc')
    },
    sortAddressAsc(){
      this.$emit('sortAddressAsc')
    },
    sortAddressDesc(){
      this.$emit('sortAddressDesc')
    },
    sortCreatedAsc(){
      this.$emit('sortCreatedAsc')
    },
    sortCreatedDesc(){
      this.$emit('sortCreatedDesc')
    }
  }
}
</script>

<style scoped>

</style>