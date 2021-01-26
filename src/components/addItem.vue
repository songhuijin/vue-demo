<template>
  <div class="addItem">
    <a-textarea
      v-model="value"
      style="width:800px"
      placeholder=""
      :auto-size="{ minRows: 3, maxRows: 5 }"
    />
    <div class="btnGroup ">
      <div class="btn addBtn" @click="handle('add')">增加</div>
      <div class="btn delBtn" @click="handle('del')">删除</div>
    </div>
  </div>
</template>
<script>
export default {
  name:'addItem',
  data(){
    return{
      value:''
    }
  },
  methods:{
    handle(type){
      let obj = {
        type:type,
        value:this.value
      }
      this.$emit('handleAction',obj)
      if(type == 'add'){
        this.value = ''
      }
    }
  }
}
</script>
<style scoped>
.addItem{
  text-align: center;
}
.btnGroup{
  text-align: center;
}
.btn{
  display: inline-block;
  color: #ffffff;
  padding:10px 30px;
  margin:10px;
  border-radius: 40px;
  cursor: pointer;
}
.addBtn{
  background: #5391FF;
}
.delBtn{
  background:#FFA500;
}
</style>