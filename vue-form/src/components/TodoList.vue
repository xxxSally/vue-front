<template>
    <div>
        <ul>
            <li v-for="(todoItem, index)  in todoItems" v-bind:key="todoItem" class="shadow">
                <i class="checkBtn fas fa-check" v-bind:class="{checkBtnCompleted: todoItem.complete}" @click="toggleComplete(todoItem, index)"></i>
                <span v-bind:class="{textCompleted: todoItem.completed}">{{ todoItem.item }}</span>
                <span class="removeBtn" @click="removeTodo(todoItem, index)">
                    <i class="fas fa-trash-alt"></i>
                </span>
            </li>
        </ul>
    </div>
</template>

<script>
    export default {
        name: 'todo-list',
        data() {
            return {
                todoItems: []
            }
        },
        methods: {
            removeTodo (todoItem, index) {
                localStorage.removeItem(todoItem);
                this.todoItems.splice(index, 1);
            },
            toggleComplete (todoItem) {
                todoItem.completed = !todoItem.completed;
                //로컬 스토리지 데이터 갱신
                localStorage.removeItem(todoItem.item);
                localStorage.setItem(todoItem.item, JSON.stringify(todoItem));
            }
        },
        created: function () {
            //뷰 인스턴스가 생성되자마자 실행되는 lifecycle 훅
            if(localStorage.length > 0) {
                for(var i = 0 ; i<localStorage.length ; i++){
                    if(localStorage.key(i) !== 'loglevel:webpack-dev-server'){
                        // this.todoItems.push(localStorage.key(i));
                        
                        //완료버튼 토글을 위해 json형식으로 localStorage에 저장해 둔 걸 꺼내서 todoItems에 넣을것
                        // {"complete: false", "item": "aaa"}
                        // 이걸 json.parse하면 다시 객체 형식으로 todoItems에 push
                        this.todoItems.push(JSON.parse(localStorage.getItem(localStorage.key(i))));
                    }
                }
            }
        },
        
    }
</script>

<style scoped>
.checkBtn {
  line-height: 45px;
  color: #62acde;
  margin-right: 5px;
}
.checkBtnCompleted {
  color: #b3adad;
}
.textCompleted {
  text-decoration: line-through;
  color: #b3adad;
}
.removeBtn {
  margin-left: auto;
  color: #de4343;
}
ul {
  list-style-type: none;
  padding-left: 0;
  margin-top: 0;
  text-align: left;
}
li {
  display: flex;
  min-height: 50px;
  height: 50px;
  line-height: 50px;
  margin: 0.5rem 0;
  padding: 0 0.9rem;
  background: white;
  border-radius: 5px;
}
</style>