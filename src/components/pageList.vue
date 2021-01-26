<template>
  <div class="wrapper">
    <add-item @handleAction="handleAction"></add-item>
    <div class="list">
      <div v-for="(item,index) in list" 
        :key="index"
        class="listItem"
        :class="{firstColor:index == 0 ,notfirstColor:index != 0}">
          {{item.remark}}
          <span class="numStyle">{{getNum(item.remark)}}</span>
          <div class="itemDel" @click="handleDel(index)">删除</div>
      </div>
    </div>
  </div>
</template>
<script>
import AddItem from './addItem.vue'
export default {
  name:'pageList',
  components:{
    AddItem
  },
  data(){
    return{
      list:[
        {
          remark:'Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua'
        },
        {
          remark:'Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua'
        },
        {
          remark:'测试'
        },
        {
          remark:'测测试试'
        }
      ]
    }
  },
  methods:{
    getNum(data){
      return data.length
    },
    handleDel(index){
      this.list.splice(index,1)
    },
    handleAction(data){
      if(data.type == 'del'){
        this.list.pop()
      }else if(data.type == 'add'){
        this.list.push({remark:data.value})
      }
    }
  }
}
</script>
<style scoped>
.wrapper{
  margin:0 280px;
}
.firstColor{
  background:#4E3FE5;
  color:#ffffff;
}
.notfirstColor{
  background:#F4F4F4;
}
.list{
  display: flex;
  flex-wrap:  wrap;
}
.listItem{
  width:300px;
  padding:15px 15px 60px;
  position: relative;
  margin:10px 10px 0 0 ;
  height:230px ;
  overflow: hidden;
}
.itemDel{
  position: absolute;
  right: 15px;
  bottom: 15px;
  background: #FFA500;
  border-radius: 5px;
  padding:3px 15px;
  color:#ffffff;
  cursor: pointer;
}
.numStyle{
  display: inline-block;
  margin-left:5px;
}
</style>