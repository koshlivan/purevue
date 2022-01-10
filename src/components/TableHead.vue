<template>
  <table>
    <tr>
      <th><input type="checkbox" name="selectAll" v-model="checkAll"></th>
      <th>
        <div>
          <h5 class="col-name">Preview</h5>
        </div>

      </th>
      <th>
        <div>
          <h5 class="col-name">Name</h5>
        </div>
        <div class="arrows">
          <span class="material-icons" @click="sortNameAsc">arrow_drop_up</span>
          <span class="material-icons" @click="sortNameDesc">arrow_drop_down</span>
        </div>
      </th>
      <th>
        <div>
          <h5 class="col-name">Email</h5>
        </div>
        <div class="arrows">
          <span class="material-icons" @click="sortEmailAsc">arrow_drop_up</span>
          <span class="material-icons" @click="sortEmailDesc">arrow_drop_down</span>
        </div>
      </th>
      <th>
        <div>
          <h5 class="col-name">Address</h5>
        </div>
        <div class="arrows">
          <span class="material-icons" @click="sortAddressAsc">arrow_drop_up</span>
          <span class="material-icons" @click="sortAddressDesc">arrow_drop_down</span>
        </div>
      </th>
      <th>
        <div>
          <h5 class="col-name">Created</h5>
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
//@change="$emit('setAllChecked')"
export default {
  name: "TableHead",
  props: ['allCheck'],
  emits:[
    'setAllChecked',
    'sortNameAsc',
    'sortEmailAsc',
    'sortEmailDesc',
    'sortAddressAsc',
    'sortAddressDesc',
    'sortCreatedAsc',
    'sortCreatedDesc',
    'update:checkAllLines'
  ],
  computed:{
    checkAll:{
      get(){
        return this.allCheck
      },
      set(value){
        this.$emit('update:checkAllLines', value)
      }
    }
  },
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

.col-name {
  padding-top: 0.5rem;
}
</style>