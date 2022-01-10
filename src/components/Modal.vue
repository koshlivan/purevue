<template>
  <div id="field">
    <div class="card">
      <form class="edit-form" @submit.prevent="onSubmit" >
        <div class="head">
          <h2>Create Contact</h2>
          <h2 class="close-butt" @click="$emit('modal-close')"><span class="material-icons">clear</span></h2>
        </div>
        <div class="inputs">
          <div class="vert">
            <div class="row align-items-center justify-content-around ">
              <label class="edLabel col-4">Name</label>
              <input type="text"
                     class="edEdit col-8"
                     name="name"
                     v-model="name"
                     placeholder="Please enter yor name" >
            </div>
            <div class="row align-items-center justify-content-around ">
              <label class="edLabel col-4">Email</label>
              <input type="email"
                     class="edEdit col-8"
                     name="email"
                     v-model="email"
                     placeholder="test@domain.com" >
            </div>
            <div class="row align-items-center justify-content-around ">
              <label class="edLabel col-4">Address</label>
              <input type="text"
                     class="edEdit col-8"
                     name="address"
                     v-model="address"
                     placeholder="Address" >
            </div>
          </div>
          <div class="foto">
            <img :src="photoPresence" alt="&#9587;">

          </div>
        </div>
        <div class="finish">
          <button id="close" type="button" @click="$emit('modal-close')">close</button>
          <button id="save" type="submit"><span class="material-icons">check</span>save changes</button>
        </div>
      </form>
    </div>

  </div>
</template>

<script>
export default {
  name: "Modal",

  props: [
      'modelName',
      'modelEmail',
      'modelAddress',
      'takeName',
      'takeAddress',
      'takeEmail',
      'takePhotopath'
  ],

  emits: [
      'update:modelName',
      'update:modelEmail',
      'update:modelAddress',
    'submitted',
    'modal-close'
  ],

  methods:{
    onSubmit(){
      this.$emit('submitted',{
        name: this.name,
        email: this.email,
        address: this.address,
        photo: this.photo,
      });
    },
  },

  computed:{
      name: {
        get(){
          return this.takeName
        },
        set(newValue){
          this.$emit('update:modelName', newValue)
        }
      },
    email:{
        get(){
          return this.takeEmail
        },
        set(newValue){
          this.$emit('update:modelEmail', newValue)
        }
    },
    address:{
        get(){
          return this.takeAddress
        },
        set(newValue){
          this.$emit('update:modelAddress', newValue)
        }
    },
    sentPhotopath:function(){
      return this.takePhotopath
    },
    photoPresence: function(){
        if(this.sentPhotopath==''){
          return 'assets/none.png'
        }
        return this.sentPhotopath
    }
  },

  data(){
    return{
      // name: this.sentName,
      // email: this.sentEmail,
      // address: this.sentAddress,
      photo: this.photoPresence,
    }
  }
}
</script>

<style scoped>
.head {
  margin-top: 1rem;
}
.foto{
  margin: 0.5rem 0 0.5rem 1.5rem;
  display:flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: stretch;
}
.foto img{
  min-height: 80%;
}
</style>