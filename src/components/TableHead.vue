<template>
  <table>
    <tr>
      <th><input type="checkbox" name="selectAll" v-model="checkAll"></th>
      <th>
        <div>
          <h5 class="col-name">Preview</h5>
        </div>

      </th>
      <th class="sortable" @click="sortName">
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
<!--        <div class="arrows">-->
<!--          <span class="material-icons" @click="sortEmailAsc">arrow_drop_up</span>-->
<!--          <span class="material-icons" @click="sortEmailDesc">arrow_drop_down</span>-->
<!--        </div>-->
      </th>
      <th class="sortable" @click="sortAddress">
        <div>
          <h5 class="col-name">Address</h5>
        </div>
        <div class="arrows">
          <span class="material-icons" @click="sortAddressAsc">arrow_drop_up</span>
          <span class="material-icons" @click="sortAddressDesc">arrow_drop_down</span>
        </div>
      </th>
      <th class="sortable" @click="sortCreated">
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
    'update:checkAllLines',
    'sort',
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
    sortName(){
      this.$emit('sort', 'name')
    },
    sortAddress(){
      this.$emit('sort', 'address')
    },
    sortCreated(){
      this.$emit('sort', 'created')
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

table{
  width: 100%;
}
table tr {
  background-color: rgba(173, 173, 173, 0.2);
  display: flex;
  justify-content: space-between;
  align-items: stretch;
  min-height: 3rem;

}
th{
  min-height: 2rem;
  margin: 0.5rem auto;
  min-width: 14%;
  padding-left: 1rem;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: stretch;
}
th h5{
  vertical-align: middle;
}
.sortable:hover{
  cursor: pointer;
  background: linear-gradient(rgba(173, 173, 173, 0.2), white, rgba(173, 173, 173, 0.2));
}
.sortable:active{
  background: linear-gradient(rgba(150, 150, 150, 0.2), rgba(200, 200, 200, 0.6), rgba(150, 150, 150, 0.2));
}
.arrows{
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
.arrows span:nth-child(2n+1){
  margin: 0;
  padding: 0;
  vertical-align: text-bottom;
  font-size: 16px;
}
.arrows span:nth-child(2n){
  margin: 0;
  padding: 0;
  vertical-align: text-top;
  font-size: 16px;
}
.arrows span:hover{
  color: red;
  text-shadow: 1px 2px 3px black;
  cursor: pointer;
}
.arrows span:active{
  color: #5e0000;
  text-shadow: 0 0 3px black;
  cursor: pointer;
}

.arrow-active{
  color: #5e0000;
  text-shadow: 0 0 3px black;
}
</style>