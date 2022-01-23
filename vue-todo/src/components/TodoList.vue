<template>
  <div>
    <transition-group name="list" tag="ul">
        <li v-for="(todoItem,index) in getTodoItems" :key="todoItem.item" class="shadow">
          <i class="fas fa-check checkBtn" :class="{checkBtnCompleted:todoItem.completed}" @click="toggleComplete({todoItem,index})"></i>
          <span :class="{textCompleted:todoItem.completed}">{{todoItem.item}}</span>
          <span class="removeBtn" @click="removeTodo({todoItem,index})">
            <i class="fas fa-trash" ></i>
          </span>
        </li>
    </transition-group>
  </div>
</template>

<script>
import {mapGetters, mapMutations} from 'vuex'

export default {
  computed:{
    ...mapGetters(['getTodoItems'])
  },
  methods:{
    ...mapMutations({
      removeTodo : 'removeOneItem', // 보내는 파라메터는 자동으로 전달된다. {todoItem,index}
      toggleComplete: 'compltItem'  
    })

    // ...mapMutations(['removeOneItem','compltItem']),
    // 이렇게도 선언이 가능. 대신, @click = "removeOneItem" / @clcick = "compltItem" 이렇게 연결해 줘야함

  }
    
}
</script>

<style scoped>
ul{
    list-style-type: none;
    padding-left: 0px;
    margin-top: 0px;
    text-align: left;
}
li {
    display: flex;
    min-height: 50px;
    height: 50px;
    line-height: 50px;
    margin:0.5rem 0;
    padding: 0 0.9rem;
    background:white;
    border-radius: 5px;
}
.checkBtn{
    line-height: 45px;
    color:#62acde;
    margin-right: 5px;
}
.checkBtnCompleted{
    color:#b3adad;
}
.textCompleted{
    text-decoration: line-through;
    color:#b3adad;
}
.removeBtn{
    margin-left: auto;
    color:#de4343
}
.list-enter-active, .list-leave-active {
transition: all 1s;
}
.list-enter, .list-leave-to /* .list-leave-active below version 2.1.8 */ {
opacity: 0;
transform: translateY(30px);
}
/* 리스트 아이템 트랜지션 효과 */

.list-enter-active, .list-leave-active {
  transition: all 1s;
}
.list-enter, .list-leave-to /* .list-leave-active below version 2.1.8 */ {
  opacity: 0;
  transform: translateY(30px);
}
</style>