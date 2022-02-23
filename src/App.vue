<template>
  <div id="app">
     <h1>ToDoList 待辦事項</h1>
  <input id="input_name" v-model="inputtodo" placeholder="輸入待辦事項...">
  <span class="addbtn" v-on:click="addnew">+新增</span>
  <div class="todolist">
    <label>待辦事項：</label>
    <br>
    <ul style="none">
    <li v-for="(t,id) in todolist" :key="t.id" class="todo_list">
      {{id+1}}.{{t.todo}}<div class="remove" v-on:click="complete(id)">finish</div>
    </li>
  </ul>
  </div>
  <div class="finlist">
    <label>已完成：</label>
    <ul  style="none">
      <li v-for="(ft,id) in finlist" :key="ft.id" class="fin_list">
      {{id+1}}.{{ft.findo}}   {{ new Date().getFullYear() }}/{{ new Date().getMonth()+1 }}/{{ new Date().getDate() }}  {{ new Date().getHours() }}:{{ new Date().getMinutes() }}
      <div class="remove" v-on:click="del(id)">Delete</div>
      </li>
    </ul>
  </div>
 </div>
</template>

<script>



export default {
  name: 'App',
  data() {
    return {
      inputtodo: "",
      todolist: [],
      finlist: [],
    }
  },
  methods: {
    addnew: function(){
      this.todolist.push({
        todo: this.inputtodo
      });
      this.inputtodo = "";
    },
    complete: function(id){
      this.finlist.push({
        findo: this.todolist[id].todo
      });
      this.todolist.splice(id,1);
    },
    del: function(id){
      this.finlist.splice(id,1);
    },

  }
}
</script>

<style lang="scss">
* {
  position: relative;
}

html,body {
  width: 100%;
  height: 100%;
  margin: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #ffc954;
}

#app {
  padding: 20px;
  border: solid 4px #333;
  background-color: #f3f3f3;
}
h1 {
  padding: 20px;
  margin-top: -20px;
  margin-left: -20px;
  margin-right: -20px;
  border-bottom: solid 4px #333;
  box-sizing: border-box;
  background-color: #ff3d4a;
  color: #f3f3f3;
  font-weight: 600;
}
#input_name {
  margin-bottom: 15px;
}

.todolist {
  border: solid 1px;
  padding: 10px;
  margin-bottom: 15px;
}
.addbtn {
  cursor: pointer;
  margin-left: 10px;
  padding: 5px;
  border: solid 3px #333;

  &:hover {
    background-color: red;
    color: white;
  }
}
ul {
  list-style: none;
}
li {
  display: flex;
}
.remove {
  position: absolute;
  right: 10px;
  cursor: pointer;
  width: 50px;
  text-align: center;
  &:hover {
    background-color: red;
    color: white;
  }
}
</style>