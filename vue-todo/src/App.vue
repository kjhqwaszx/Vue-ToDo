<template>
  <div id="app">
    <TodoHeader></TodoHeader>
    <TodoInput></TodoInput>
    <TodoList></TodoList>
    <TodoFooter></TodoFooter>
  </div>
</template>

<script>
import TodoHeader from './components/TodoHeader.vue'
import TodoList from './components/TodoList.vue'
import TodoInput from './components/TodoInput.vue'
import TodoFooter from './components/TodoFooter.vue'

export default {

  components:{
    // ES6 축약 기능으로 KEY, VALUE가 동일하면 축약 가능
      // 'TodoHeader': TodoHeader,
      // 'TodoList': TodoList,
      // 'TodoInput': TodoInput,
      // 'TodoFooter': TodoFooter
      TodoHeader,
      TodoList,
      TodoInput,
      TodoFooter
  },

  data(){
    return{
      todoItems: []
    }
  },
  methods:{
    
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
