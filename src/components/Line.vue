<template>
    <div class="cell">
      <div><input type="checkbox" name="selectOne" :checked="thisCheckbox" @change="checkboxChanged"></div>
      <div><img class="preview" :src="user.photopath" alt="X"></div>
      <div><h6>{{user.name}}</h6></div>
      <div><h6>{{user.email}}</h6></div>
      <div><h6>{{ user.address }}</h6></div>
      <div><h6>{{ user.created }}</h6></div>
      <div style="position: relative">
        <h6 id="ellips" @click="options">&#x22EE;</h6>
        <div id="options" v-show="showOptions">
          <h6 @click="showModal"><span class="material-icons">menu</span>View</h6>
          <h6 @click="singleDelete"><span class="material-icons">delete</span>Delete</h6>
        </div>
      </div>
    </div>
</template>

<script>
//import HelloWorld from "@/components/HelloWorld";

export default {
  name: "Line",
  props: [
      'isChecked',
      'isPopUp',
      'user'
  ],
  emits:[
    'showModal',
    'viewPopup',
    'singleCheckBoxSelected',
    'singleCheckBoxUnSelected',
    'singleCheckBoxChanged',
    'showFilledModal',
    'deleteOne'
  ],
  computed:{
    thisCheckbox: function(){
      //this.checkboxChanged();
      return this.isChecked
    }
  },
  methods:{
    options(){
      //this.$emit('viewPopup');
      this.showOptions=!this.showOptions;
    },
    showModal(){
      this.$emit('showFilledModal');
      this.showOptions=false;
    },
    allCheckedHandler(){
      //this.$parent.$on('allChecked', this.checkboxChanged());
    },
    checkboxChanged(){
      if(this.checkboxSelect===true){
          this.$emit('singleCheckBoxChanged', 'false');
      }
      else{
        this.$emit('singleCheckBoxChanged', 'true');
      }
      this.checkboxSelect=!this.checkboxSelect;
      console.log("emitter in line");
    },
    singleDelete(){
      this.$emit('deleteOne');
      this.showOptions=false;
    }
  },

  data(){
    return{
      showOptions: false,
      checkboxSelect: this.thisCheckbox
    }
  }
}
</script>

<style scoped>
input[type=checkbox]{
  vertical-align: center;
  margin-top: 1rem;

}
#options{
  display:flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: stretch;
  border: solid 2px black;
  box-shadow: 0 0 5px gray;
  min-width: 8rem;
  max-height: 4rem;
  z-index: 2;
  position: absolute;
  top: 1rem;
  left: 1rem;
  background-color: white;
  opacity: 100%;
}
#options h6{
  box-sizing: border-box;
  margin: 0;

  line-height: 1.5rem;
  border-bottom: solid 2px black;
}
#options h6:hover{
  background-color: rgba(173,82,14,0.24);
  cursor: pointer;
}
#options h6:active{
  background-color: rgba(91, 41, 8, 0.24);
  color: white;
  cursor: pointer;
}
#options span{
  vertical-align: middle;
  color: black;
}
#options h6:active span{
  color: red;
}
</style>