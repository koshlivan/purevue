<template>
  <div id="hat">
    <div className="hat-first">
      <h3 :title="currentDate">{{title+' - '+ currentDate}}</h3>

      <div id="myDropdown">
        <div className="myDropdown">
          <span className="material-icons">account_circle</span>
          <h5>Your Name</h5>
          <span className="material-icons">arrow_drop_down</span>
        </div>
        <div className="dropped">
          <a href="#">some text</a>
          <a href="#">some text</a>
          <hr>
          <a href="#">Exit</a>
        </div>
      </div>
    </div>
    <hr className="under-hat">
  </div>
</template>

<script>
export default {
  name: "Headder",
  props:[
    'title'
  ],
  computed: {
    currentDate(){
      return new Date().getDate()+'.'+ new Date().getMonth()+1+'.'+ new Date().getFullYear()
    }
}
}
</script>

<style scoped>
#hat {
  background-color: #f66d06;
  color: white;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-content: stretch;
}
.hat-first {
  display: flex;
  justify-content: space-between;
  align-items: stretch;
}
.hat-first h3 {
  text-transform: capitalize;
  line-height: 4rem;
  padding-left: 2rem;
  text-transform: capitalize;
}
#myDropdown {
  min-height: 2rem;
  padding: 0.2rem 1rem;
  position: relative;
  margin: 0.5rem 1rem;
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: rgba(0,0,0,0.5);
  text-align: center;
  text-transform: capitalize;
  cursor: pointer;
  transition: 200ms;
}
.myDropdown h5{
  line-height: 2rem;
  padding-top: 0.7rem;
  vertical-align: bottom;
  display: inline-block;
}
.myDropdown span{
  line-height: 3rem;
  vertical-align: middle;
  display: inline-block;
}

.dropped {
  display: none;
  min-width: 100%;
  position: absolute;
  top: 100%;
  transition: 500ms;
  box-shadow: 0 0 5px #f66d06;
  background-color: rgba(141,33,2,0.71);
  z-index: 1;
}
.dropped a{
  display: block;
  text-decoration: none;
  font-size: large;
  color: white;
}
.dropped a:hover{
  color: #d0cdcd;
  background-color: rgba(255,81,0,0.91);
}

.dropped hr{
  border: solid 3px white;
  margin: 3px 0;
}

#myDropdown:hover .dropped {
  cursor: pointer;
  display: block;
}
#myDropdown:hover{
  background-color: rgba(0,0,0,0.7);
}
.dropped:hover{
  display: block;
}
.under-hat {
  border: solid 2px white;
  margin: 3px;
  opacity: 80%;
}

</style>