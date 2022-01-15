<template>
  <div id="rrr">
    <div id="bg">
      <img src="https://w.wallhaven.cc/full/vg/wallhaven-vgdj28.jpg" alt="">
    </div>
    <div class="root">

      <div id="title-bar">
        <div>{{head}}</div>
         <a-button @click="pushThing" type="primary">添加</a-button>
      </div>

      <div id="container">

        <div class="main" id="sidebar" >
          <todo-item v-for="item in ds "  :title="item.title" :date="item.date" :msg="item.msg" ></todo-item>
        </div>

        <div class="main" id="content">
            {{ds}}

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
      ds:[
        {
          title:"thing ",
          msg:"jin tian chi le ni ma bi ",
          date: "12:30"
        }
      ]
    }
  },
  // created() {
  //   for(let i=0;i<10;i++){
  //     this.ds.push(
  //         {
  //           title:"thing "+i,
  //           msg:"jin tian chi le ni ma bi ",
  //           date: new Date().toLocaleString()
  //         },
  //     )
  //   }
  //
  // },
  computed:{
    getNow(){
      return new Date().toLocaleString()
    }
  },
  methods:{
    pushThing(){
      this.ds.push(
          {
            title:"thing ",
            msg:"jin tian chi le ni ma bi ",
            date: new Date().toLocaleString()
          },
      )
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
  position: fixed;
  top: 5px;
  display: flex;
  justify-content: center;
  height: 35px;
  width: 100%;
  background: #2c3e50;
  color:  white;
  z-index: 3;
}
#title-bar div{
  text-align: center;
}
#title-bar button{
  position: relative;
  /*display: block;*/
  left: 430px;
  border: antiquewhite solid;
  border-radius: 5px;
  /*background: black;*/
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
  padding: 8px;
  position: relative;
  display: flex;
  flex-direction: column;
  overflow: hidden;
  justify-content: flex-start;
  top: 10px;
  left: 10px;
  width: 20%;
  border: aqua solid;
  border-radius: 5px;
  height: 520px;
  /*background: #2c3e50;*/
  flex-shrink: 0;
}
#container{
  display: flex;
  flex-direction: row;
}

#content{
  position: relative;
  top: 8.5%;
  left: 35px;
  border: aqua solid;
  border-radius: 15px;
  width: 73%;
  height: 520px;
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