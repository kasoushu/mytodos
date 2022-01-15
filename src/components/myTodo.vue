<template>
  <div id="rrr">
    <div id="bg">
      <img src="https://w.wallhaven.cc/full/vg/wallhaven-vgdj28.jpg" alt="">
    </div>
    <div class="root">

      <div id="title-bar">
        {{head}}
      </div>

      <div id="container">

        <div class="main" id="sidebar" >
          <todo-item v-for="item in ds "  :title="item.title" :date="item.date" :msg="item.msg" ></todo-item>
        </div>

        <div class="main" id="content">


        </div>


      </div>


    </div>

  </div>
</template>

<script>
import todoItem from "@/components/todoItem";

export default {
  name: "myTodo",
  components:{
    todoItem
  },
  data(){
    return {
      head:"TODOS!!!!",
      ds:[]
    }
  },
  created() {
    for(let i=0;i<10;i++){
      this.ds.push(
          {
            title:"thing "+i,
            msg:"jin tian chi le ni ma bi ",
            date: new Date().toLocaleString()
          },
      )
    }

  },
  computed:{
    getNow(){
      return new Date().toLocaleString()
    }
  }
}
</script>

<style scoped>
#bg{
  position: fixed;
  top: 0;
  left: 0;
  height: 100%;
  width: 100%;
  fill-opacity: 0.2;
  /*z-index: 1;*/

}
#title-bar{
  /*padding-top:40px;*/
  position: relative;
  top: 35px;
  display: block;
  width: 100%;
  background: #2c3e50;
  color:  white;
  z-index: 3;
  text-align: center;
}
#rrr{
  width: 100%;
  position: fixed;
  top: 0;
  left: 0;
  height: 100%;
  display: flex;
  /*z-index: 2;*/

}
#sidebar{
  margin-top: 25px;
  position: relative;
  top: 25px;
  left: 10px;
  /*width: 100%;*/
  flex-shrink: 0;
}
#container{
  /*display: flex;*/
  /*flex-direction: row;*/
}

#content{
  position: relative;
  top: 35px;
  width: 80%;
  height: 300px;
  background: antiquewhite;
}

.root{
  margin: 5% auto auto;
  display: flex;
  flex-direction: column;
  justify-content: center;
  opacity: 0.8;
  width: 1000px;
  height: 600px;
  overflow: hidden;
  -webkit-backdrop-filter: blur(64px);
  backdrop-filter: blur(64px);
  z-index: 2;
}





</style>