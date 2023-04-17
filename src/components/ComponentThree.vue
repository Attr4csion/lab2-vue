<template>
    <div>
        <input 
            type="text" 
            class="todo-input" 
            placeholder="Что надо сделать?"
            v-model="newTodo"
            @keyup.enter="addTodo"
        >
        <div 
            v-for="(todo,index) in todos" :key="todo.id"
            class="todo-item"
        >
            <div class="todo-item-left">
                <input type="checkbox"  v-model="todo.completed" >
                <div 
                    v-if="!todo.editing"
                    @dblclick="editTodo(todo)"
                    class="todo-item-label"
                    :class="{completed:todo.completed}"
                    >
                    {{ todo.title }}
                </div>
                <input 
                    v-else 
                    class="todo-item-edit"
                     type="text" 
                     v-model="todo.title"
                     @blur="doneEdit(todo)"
                     @keyup.enter="doneEdit(todo)"
                     @keyup.esc="cancelEdit(todo)"
                >
            </div>
            <div class="remove-item" @click="removeTodo(index)">
                &times;
            </div>
        </div>
    </div>
</template>

<script>
export default{
    data(){
        return{
            newTodo:'',
            idForTodo:3,
            beforeEdit:'',
            todos:[
                {
                    'id':1,
                    'title':'Сходить в магазин',
                    'completed':false,
                    'editing':false
                },
                {
                    'id':2,
                    'title':'Покормить собаку',
                    'completed':false,
                    'editing':false

                }
            ]
        }
    },
    methods:{
        addTodo(){
            if(this.newTodo.trim().length == 0){
                return
            }
          this.todos.push({
            id:this.idForTodo,
            title: this.newTodo,
            completed:false,
          })
          this.newTodo ='',
          this.idForTodo++
        },
        removeTodo(index){
            this.todos.splice(index,1)
        },
        editTodo(todo){
            this.beforeEdit=todo.title,
            todo.editing = true
        },
        doneEdit(todo){
            if(todo.title.trim().length == 0){
                todo.title=this.beforeEdit
            }
            todo.editing = false
        },
        cancelEdit(todo){
            todo.title=this.beforeEdit,
            todo.editing=false
        }
    }
}
</script>

<style scoped>
.todo-input{
    width: 100%;
    padding: 10px 18px ;
    font-size: 18px;
    margin-bottom: 16px;
}
.todo-item{
    margin-bottom: 12px;
    display: flex;
    align-items: center;
    justify-content: space-between;
}
.remove-item{
    cursor:pointer;
    margin-left: 14px;
}
.remove-item:hover{
    color:red;
}
.todo-item-left{
    display: flex;
    align-content: center;
}
.todo-item-label{
    padding: 10px;
    border: 1px solid white;
    margin-left: 12px;
}
.todo-item-edit{
    font-size: 24px;
    color:#2c3e50;
    margin-left: 12px;
    width: 100%;
    padding: 10px;
    border: 1px solid #ccc;
    font-family: 'Avenir', Arial, Helvetica, sans-serif;
}

.completed{
    text-decoration: line-through;
    color:grey;
    }
.check_hidden{
    visibility: hidden;
}
</style>