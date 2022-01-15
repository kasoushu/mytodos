<template>
  <div id="item">
    <div class="it" id="it1">
      {{title}}
    </div>
    <div id="it2" class="it">
      <span id="sp1">{{date}}</span>
      <span id="sp2" >{{msg}}</span>
    </div>
  </div>
</template>

<script>
export default {
  name: "todoItem",
  data(){
    return {

    }
  },
  props:{
    title:String,
    msg:String,
    date:String,
  }
}
</script>

<style scoped>
.it{

}
#item{
  display: flex;
  background: antiquewhite;
  flex-flow: column;
  /*padding-top: 15px;*/
  margin: 5px auto;
  width: 100%;
  height: 50px;
  max-width: 220px;
  border: aqua solid ;
  border-radius: 10px;
   flex-wrap: nowrap;
}
#it2{
  display: inline-flex;
  flex-direction: row;
  justify-content: flex-start;
  font-size: x-small;
  flex-wrap: nowrap;
  overflow: hidden;
  padding-top: 5px;
}
#it1{
  text-align: left;
  padding-left: 10%;
}
#sp1{
  padding-left: 10px;

  white-space: nowrap;
}

#sp2{
  order: 1;
  padding-left: 15px;
  white-space: nowrap;
  flex-shrink: 0.5;
}

</style>