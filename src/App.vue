<template>
  <HelloWorld msg="Welcome to Your Vue.js App"/>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  }
}
</script>

<style>
@import url('https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css');
@import url('https://fonts.googleapis.com/icon?family=Material+Icons');

.wrapper {
  max-width: 100%;
}


.holder {
  max-width: 90%;
  margin: 3rem auto;
  border: solid 2px black;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: stretch;
}

.holder h3{
  margin-left: 1rem;
  line-height: 3rem;
  vertical-align: middle;
}
.cap{
  display: flex;
  justify-content: space-between;
  align-items: stretch;
  border-top:solid 1px gray;
  border-bottom:solid 1px gray;
}
.cap h3{
  margin-left: 1rem;
  margin-top: 0.5rem;
  margin-bottom: 0.5rem;
}
#addContact {
  background-color: #0a53be;
  color: white;
  border: solid 2px black;
  margin-right: 1rem;
  margin-top: 0.5rem;
  margin-bottom: 0.7rem;
  font-size: 20px;
  transition: 300ms;
}
#addContact:hover{
  background-color: #2b68c0;
  box-shadow: 0 4px 5px gray;
}
#addContact:active{
  background-color: #063272;
  box-shadow: 0 1px 2px gray;
  color: #ad9799;
}
#addContact span{
  vertical-align: text-bottom;
}

#field {
  min-width: 100%;
  min-height: 100vh;
  background-color: rgba(105, 105, 105, 0.7);
  display: flex;
  justify-content: center;
  align-content: center;
  z-index: 4;
  position: absolute;
  top: 0;

}
.card {
  min-width: 30%;
  max-width: 40%;
  height: 25rem;
  border-radius: 1rem;
  box-shadow: 0 0 5px rgba(10, 10, 10, 0.8);
  position: absolute;
  top: 50%;
  left:  50%;
  transform: translate(-50%, -50%);
  opacity: 100%;
}
.edit-form {
  display: flex;
  min-height: 100%;
  flex-direction: column;
  justify-content: space-around;
  align-items: stretch;
  opacity: 100%;
}
.edit-form div:nth-child(2n+1){
  min-height: 20%;
}
.edit-form div:nth-child(2n){
  min-height: 60%;
}

.head{
  display: flex;
  justify-content: space-between;
  align-items: stretch;
  margin-top: 1rem;
  padding-top: 1rem;
}
.head h2 {
  margin: 1rem;
}
.head img{
  max-height: 80%;
  margin-right: 0.5rem;
  margin-top: 0.5rem;
  transition: 300ms;
}
.head img:hover{
  max-height: 85%;
  cursor: pointer;
  box-shadow: 0 0 3px gray;
}
.head img:active{
  max-height: 85%;
  cursor: pointer;
  box-shadow: 0 0 5px red;
}
.close-butt{
  margin-right: 0.5rem;
  margin-top: 0.5rem;
  transition: 300ms;
}
.close-butt span:hover{
  cursor: pointer;
  box-shadow: 0 0 3px gray;
}

.inputs {
  display: flex;
  justify-content: space-around;
  align-items: stretch;
}

.vert {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: stretch;
  max-width: 60%;
}
.vert label {
  padding-left: 2rem;
}
.vert input {
  border: solid 2px black;
}

.foto{
  display: flex;
  max-width: 40%;
  justify-content: center;
  align-items: center;
}

.foto img{
  max-height: 95%;
  max-width: 95%;
}

.finish {
  display: flex;
  justify-content: flex-end;
  align-items: stretch;
  margin: 2rem 0;
}

.finish button{
  max-height: 2.5rem;
}

.finish button:nth-child(2n){
  margin-right: 4rem;
  margin-left: 1rem;
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
.cell{
  margin: 1rem 0;
  display: flex;
  justify-content: space-between;
  align-items: stretch;
  min-height: 3rem;
  max-height: 4rem;
  text-align-all: left;
  padding-left: 1rem;

}
.cell img{
  max-height: 3rem;
  max-width: 4rem;
}
.cell h6{
  text-align: left;
  text-transform: capitalize;
  vertical-align: center;
  line-height: 3rem;
}
.cell>div{
  min-width: 14%;
}
.cell:hover{
  background-color: rgba(173,82,14,0.24);

}

#ellips:hover{
  cursor: pointer;
}

#save {
  background-color: #0a53be;
  color: white;
  border: solid 2px black;
  font-size: 20px;
  text-transform: uppercase;
}
#save span{
  vertical-align: text-bottom;
}
#close {
  background-color: #808080;
  color: white;
  border: solid 2px black;
  font-size: 20px;
  text-transform: uppercase;
}

#delContact{
  background-color: #be0a10;
  color: white;
  border: solid 2px black;
  margin-right: 1rem;
  margin-top: 0.5rem;
  margin-bottom: 0.7rem;
  font-size: 20px;
  transition: 300ms;
}
#delContact span{
  vertical-align: text-bottom;
  color: white;
}
#delContact:hover{
  background-color: #bd151b;
  box-shadow: 0 4px 5px gray;
}
#delContact:active{
  background-color: #880f13;
  box-shadow: 0 1px 2px gray;
  color: #ad9799;
}


</style>
