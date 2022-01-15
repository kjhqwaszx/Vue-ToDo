<template>
  <div id="app">
    <TodoHeader></TodoHeader>
    <TodoInput @addItem="addOneItem"></TodoInput>
    <TodoList :propsdata="todoItems" @removeItem="removeOneItem" @completeItem="compltItem"></TodoList>
    <TodoFooter @removeAll="removeAll"></TodoFooter>
  </div>
</template>

<script>
import TodoHeader from './components/TodoHeader.vue'
import TodoList from './components/TodoList.vue'
import TodoInput from './components/TodoInput.vue'
import TodoFooter from './components/TodoFooter.vue'

export default {

  components:{
      'TodoHeader': TodoHeader,
      'TodoList': TodoList,
      'TodoInput': TodoInput,
      'TodoFooter': TodoFooter
  },

  created(){
    if(localStorage.length > 0){
      console.log(JSON.stringify(localStorage))
      for(var i=0; i<localStorage.length; i++){
        if(localStorage.key(i) !== 'loglevel:webpack-dev-server'){
          
          this.todoItems.push(JSON.parse(localStorage.getItem(localStorage.key(i))))
        }
      }
    }
  },

  data(){
    return{
      todoItems: []
    }
  },
  methods:{
    addOneItem(todoItem){

      var obj={completed:false, item: todoItem}
      localStorage.setItem(todoItem, JSON.stringify(obj))

      this.todoItems.push(obj)
    },

    removeOneItem(todoItem, index){
      localStorage.removeItem(todoItem.item)
      this.todoItems.splice(index,1)
    },

    compltItem(todoItem,index){
      this.todoItems[index].completed = !this.todoItems[index].completed

      localStorage.removeItem(todoItem.item)
      localStorage.setItem(todoItem.item, JSON.stringify(todoItem))
    },
    removeAll(){
      localStorage.clear()
      this.todoItems=[]
    }
  }
  

}
</script>

<style>
 body{
   text-align: center;
   background-color: #F6F6F6;
 }

 input{
   border-style: groove;
   width:200px;
 }
 button{
   border-style: groove;
 }
 .shadow{
   box-shadow: 5px 10px 10px rgba(0,0,0,0.03);
 }
</style>
