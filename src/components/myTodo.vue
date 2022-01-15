<template>
  <div id="rrr">
    <div id="bg">
      <img src="https://w.wallhaven.cc/full/vg/wallhaven-vgdj28.jpg" alt="">
    </div>
    <div class="root">

      <div id="title-bar">
        <div>{{head}}</div>
         <a-button @click="showModel" type="primary">添加</a-button>
            <a-modal
        v-model:visible="visible"
       title="添加备忘事项"
      :confirm-loading="isconfirm"
      @ok="pushThing"
    >
              <a-input v-model:value="input_content.title" placeholder="title" />

                  <a-textarea
                v-model:value="input_content.msg"
                placeholder="input your message here"
                :auto-size="{ minRows: 5, maxRows: 5 }"
                />
    </a-modal>
      </div>

      <div id="container">

          <a-list class="main" id="sidebar">
            <a-list-item :id="k" @click="showContent($event)" class="item" v-for="(item,k) in ds " >
              <todo-item    :title="item.title" :date="item.date" :msg="item.msg" ></todo-item>
            </a-list-item>
          </a-list>

        <div class="main" id="content">
          <a-card id="con" :title="show_content.title">
            <p>
              {{show_content.msg}}
            </p>

          </a-card>
          <p style="height: 20px; display: inline-block;position: relative;bottom: 20px">{{show_content.date}}</p>
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
      visible:false,
      isconfirm:false,
      show_content: {
        title:"todos",
        msg:"欢迎使用todos",
        date:"12：30",
      },
      input_content: {
        title:"",
        msg:"",
      },
      ds:[
      ]
    }
  },
  computed:{
    getNow(){
      return new Date().toLocaleString()
    }
  },
  methods:{
    showModel(){
      this.visible=true
    },
    showContent(event){
      let i = event.currentTarget.id
      // console.log(event.currentTarget.id)
      console.log(i)
      this.show_content.title = this.ds[i].title
      this.show_content.msg = this.ds[i].msg
      this.show_content.date = this.ds[i].date
    }
  ,
    pushThing(){
      this.isconfirm=true;
      this.ds.push(
          {
            title:this.input_content.title,
            msg:this.input_content.msg,
            date: new Date().toLocaleString()
          },
      )
      this.input_content.title=""
      this.input_content.msg=""
      this.visible=false;
      this.isconfirm=false;
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
  /*overflow: ;*/
  overflow-y: auto;
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
  text-align: left;
  background: antiquewhite;
}
#con{
  height: 100%;

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

.item{
  /*background: blue;*/
}





</style>