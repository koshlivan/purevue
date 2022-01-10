<template>
  <div class="wrapper">
    <Headder title="Contact Manager"></Headder>
    <div class="holder">
      <cap @showModal="showModal(-1)"
           @deleteSelected="remove"></cap>
      <div class="data">
          <TableHead @setAllChecked="setAllChecked"
                     :all-check="isAllChecked"
                     @update:checkAllLines="allChecked($event)"
                     @sortNameAsc="sortNameAsc"
                     @sortNameDesc="sortNameDesc"
                     @sortAddressDesc="sortAddressDesc"
                     @sortCreatedAsc="sortCreatedAsc"
                     @sortCreatedDesc="sortCreatedDesc"
                     @sortAddressAsc="sortAddressAsc"></TableHead>
          <div class="line">
            <Line v-for="(user, index) in users"
                  :key="user.number"
                  ref="lineComponent"
                  :is-checked="isAllChecked"
                  @deleteOne="deleteOne(index)"
                  @showFilledModal="showFilledModal(index)"
                  :is-pop-up="isPopUp"
                  :popup-now="popupNow"
                  :index="index"
                  @update:checkedLine="checkLines($event, index)"
                  @viewPopup="popupEventHandler($event, index)"
                  @singleCheckBoxChanged="lineSelectCheckboxEventHandler(index, $event)"
                  :user="user"></Line>
          </div>
      </div>
    </div>
  <Modal v-show="isShowModal"
         @modal-close="modalClose"
         @submitted="submitModal"
         :modelName="nameToSend"
         :modelEmail="emailToSend"
         :modelAddress="addressToSend"
         @update:modelName="nameToSend=$event"
         @update:modelEmail="emailToSend=$event"
         @update:modelAddress="addressToSend=$event"
         :take-name="nameToSend"
         :take-email="emailToSend"
         :take-address="addressToSend"
         :take-photopath="photopathToSend"
          ></Modal>
  </div>
</template>

<script>
import Headder from './Headder';
import Cap from './Cap';
import TableHead from './TableHead';
import Line from './Line';
import Modal from './Modal';

export default {
  name: 'HelloWorld',
  props: {
  },
  data(){
    return{
      users: [
        {number: '1', name: 'bob', email: 'bob@mail.ru', address: 'london', created: '12.12.20', photopath: './assets/unnamed.jpg'},
        {number: '2', name: 'bill', email: 'bill@mail.ru', address: 'paris', created: '23.12.19', photopath: './assets/index.jpeg'},
        {number: '3', name: 'john', email: 'john@mail.ru', address: 'berlin', created: '09.08.21', photopath: './assets/index.jpeg'},
        {number: '4', name: 'sean', email: 'sean@mail.ru', address: 'rome', created: '32.10.21', photopath: './assets/unnamed.jpg'},
        {number: '5', name: 'harry', email: 'harry@mail.ru', address: 'madrid', created: '09.11.21', photopath: './assets/prof.jpg'},
        {number: '6', name: 'chuck', email: 'chuck@mail.ru', address: 'madrid', created: '09.11.21', photopath: './assets/index.jpeg'},
        {number: '7', name: 'bruice', email: 'bruice@mail.ru', address: 'madrid', created: '09.11.21', photopath: './assets/prof.jpg'},
      ],
      user:{
        name:'',
        email:'',
        address:'',
        created:'',
        photopath:''
      },
      fields:{},
      isPopUp:false,
      popupNow:-1,
      nameToSend:'',
      emailToSend:'',
      addressToSend:'',
      photopathToSend:'',
      isAllChecked: false,
      isShowModal: false,
      item: -1,
      selectState: [],
      isExisted: false,
      sender: -1,
      selectedLines:[]
    }
  },

  components:{
    Headder,
    Cap,
    TableHead,
    Line,
    Modal
  },

  emits: [
    'setAllChecked',
    'showModal',
      'setAllSelect',
      'allChecked'
  ],

  computed:{
    thisDate: function(){
      return new Date().getDate()+'.'+new Date().getMonth()+'.'+new Date().getFullYear()
    },
    // nameToSend:{
    //   get(){
    //     return this.sentName
    //   },
    //   set(value){
    //     this.sentName=value
    //   }
    // },
    // emailToSend:{
    //   get(){
    //     return this.sentEmail
    //   },
    //   set(value){
    //     this.sentEmail=value
    //   }
    // },
    // addressToSend:{
    //   get(){
    //     return this.sentAddress
    //   },
    //   set(value){
    //     this.sentAddress=value
    //   }
    // },
  },

  methods:{
    /*OLD. sets all inputs in checked state*/
    setAllChecked(){
      this.isAllChecked=!this.isAllChecked;
      this.selectState=[];
      if(this.isAllChecked===true){
      for(let i=0; i<this.users.length; i++){
        this.selectState.push(i);
      }}
    },

    /*NEW. sets all inputs in checked state*/
    allChecked($event){
      if($event===true){
        this.isAllChecked=true;
        this.selectedLines=[];
        for(let i=0; i<this.users.length; i++){
          this.selectedLines.push(i);
        }
      }
      if($event===false){
        this.selectedLines=[];
        this.isAllChecked=false;
      }
      console.log(this.selectedLines);
    },

    /*delete one row by index*/
    deleteOne(index){
      this.users.splice(index, 1);
    },

    /*OLD. catch checkbox changes and add or remove it's state to array*/
    lineSelectCheckboxEventHandler(index, event){
      if(event=='true'){
       this.selectState.push(index);
        console.log('must to push');
      }
      else{

        let num=this.selectState.indexOf(index);
        this.selectState.splice(num, 1);
        console.log('must to splice');
      }
      console.log('event handler  '+event);
      console.log(this.selectState);
      console.log(this.selectedLines);
    },

    /*manages selected rows array*/
    checkLines($event, index){
      if($event===true){
      this.selectedLines.push(index);
        console.log('event: '+$event+' status: add');
      }
      if($event===false){
        let needIndex=this.selectedLines.indexOf(index);
        this.selectedLines.splice(needIndex, 1);
        console.log('event: '+$event+' status: remove')
      }
      console.log(this.selectedLines)
    },

    /*empty modal window for adding a new user*/
    showModal(index){
      if(index<0) {
        this.emptyUser();
        this.isShowModal = true;
      }
    },

    /*close modal*/
    modalClose(){
      this.isShowModal=false;
      this.isPopUp=false;
      this.emptyUser();
    },

    /*empty properties of user*/
    emptyUser(){
      this.isExisted= false;
      this.sender= -1;
      this.nameToSend='';
      this.emailToSend='';
      this.addressToSend='';
      this.photopathToSend='';
    },

    /*opens modal window with filled inputs with information of user*/
    showFilledModal(index){
      this.isExisted=true;
      this.sender=index;
      this.nameToSend=this.users[index].name;
      this.emailToSend=this.users[index].email;
      this.addressToSend=this.users[index].address;
      this.photopathToSend=this.users[index].photopath;
      this.isShowModal = true;
    },

    /*save user from modal window*/
    submitModal(data){
      let newUser={
        name: data.name,
        email: data.email,
        address: data.address,
        created: this.thisDate,
        photopath: 'assets/none.png'
      }
      if(this.isExisted===true){
            let user=this.users[this.sender];
            user.name=newUser.name;
            user.email=newUser.email;
            user.address=newUser.address;
          }
      else{
        this.users.push(newUser);
      }
      this.modalClose();
      console.log(this.fields);
    },

    /*toggle popup menu*/
    popupEventHandler($event, index){
      if(!$event){
        this.isPopUp=!this.isPopUp
      }
      else{
        this.isPopUp=true
      }
      if(index!=this.popupNow){
        this.isPopUp=true;
      }
      this.popupNow=index;
      console.log('catch popup + '+this.isPopUp+' '+index+' '+this.popupNow);
    },

    /*delete selected users by pressing one button*/
    remove(){
      //for(let i=0, k=0; i<this.selectState.length; i++, k++){
      for(let i=0, k=0; i<this.selectedLines.length; i++, k++){
        let deleted=Number.parseInt(this.selectedLines[i])-k;
        this.deleteOne(deleted);
      }
      this.selectedLines=[];
    },

    /*sort ascendingly by key*/
    sortAscBy(key){
      return this.users.sort(function(a, b)
      {
        let x = a[key];
        let y = b[key];
        return ((x < y) ? -1 : ((x > y) ? 1 : 0));
      });
    },

    /*sort descendingly by key*/
    sortDescBy(key){
      return this.users.sort(function(a, b)
      {
        let x = a[key];
        let y = b[key];
        return ((x < y) ? 1 : ((x > y) ? -1 : 0));
      });
    },

    sortNameAsc(){
      this.sortAscBy('name');
    },

    sortNameDesc(){
      this.sortDescBy('name');
    },

    sortAddressAsc(){
      this.sortAscBy('address');
    },

    sortAddressDesc(){
      this.sortDescBy('address');
    },

    /*sort by date ascendingly and descendingly*/
    sortCreated(method){
      let more;
      let less;
      if(method===true){
        more=1;
        less=-1;
      }
      else{
        more=-1;
        less=1;
      }
      return this.users.sort(function(a, b) {
        let x = a['created'].split('.');
        let y = b['created'].split('.');

        if (x[2] < y[2]) {
          return less;
        } else if (x[2] > y[2]) {
          return more;
        } else {
          if (x[1] < y[1]) {
            return less;
          } else if (x[1] > y[1]) {
            return more;
          } else {
            if (x[0] < y[0]) {
              return less;
            } else if (x[0] > y[0]) {
              return more;
            } else {
              return 0;
            }
          }
        }
      })
    },

    sortCreatedAsc(){
      this.sortCreated(true);
    },
    sortCreatedDesc(){
      this.sortCreated(false);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
