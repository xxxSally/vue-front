<template>
    <div>
        <input type="text" v-model="newTodoItem" v-on:keyup.enter="addTodo"/>
        <span class="addContainer" v-on:click="addTodo">
        <i class="fas fa-plus addBtn"></i>
    </span>
    </div>
</template>

<script>
    export default {
        name: 'todo-input',
        data: function() {
            return {
                newTodoItem: "",
                testItem: "",
            }
        },
        methods: {
            addTodo () {
                console.log(this.newTodoItem);
                
                //단순히 입력값을 넣는 거 말고 체크 여부를 함께 포함한 객체를 넣어줄 것
                // todolist 컴포넌트 개발하면서 체크 여부가 추가가 됨
                let obj = {};
                obj.complete = false;
                obj.item = this.newTodoItem
                //객체를 json을 string 으로 쭉 넣어주는듯
                localStorage.setItem(this.newTodoItem, JSON.stringify(obj));
                this.clearInput();
            },
            clearInput: function() {
                this.newTodoItem = "";
            }
        }
    }
</script>

<style scoped>
input:focus {
  outline: none;
}
.inputBox {
  background: white;
  height: 50px;
  line-height: 50px;
  border-radius: 5px;
}
.inputBox input {
  border-style: none;
  font-size: 0.9rem;
}
.addContainer {
  float: right;
  background: linear-gradient(to right, #62EAC6, #32CEE6);
  display: block;
  width: 3rem;
  border-radius: 0 5px 5px 0;
}
.addBtn {
  color: white;
  vertical-align: middle;
}
</style>