<template>
  <div>
    <input type="text"
           class="todo-input"
           placeholder="What needs to be done..."
           v-model="newTodo"
           @keyup.enter="addTodo">
    </input>
    <div v-for="(todo, index) in todos"
         :key="todo.id"
         class="todo-item">
         <div>    
            {{ todo.title }}
        </div>
        <div class="remove-item"
             @click="removeTodo(index)">
            <a>&times;</a>
        </div>
    </div>       
    </div>
  </div>
</template>

<script>
export default {
  name: 'todo-list',
  data () {
    return {
      newTodo: '',
      idForTodo: 3,
      todos: [
          {
              'id': 1,
              'title': 'Finnish vue screencast',
              'completed': false
          }, 
           {
              'id': 2,
              'title': 'Take over world',
              'completed': false
          }
      ]
    }
  },
  methods: {
      addTodo() {
          if (this.newTodo.trim().length === 0 ) {
              return;
          }  
          this.todos.push({
              id: this.idForTodo,
              title: this.newTodo,
              completed: false
          });

          this.newTodo = '';
          this.idForTodo++;
      },

      removeTodo(index) {
          this.todos.splice(index, 1);
      }
  }
}
</script>

<style>

    .todo-input {
        width: 100%;
        padding: 10px 18px;
        font-size: 18px;
        margin-bottom: 16px;
    }

    .todo-item {
        margin-bottom: 12px;
        display: flex;
        align-items: center;
        justify-content: space-between;
    }

    .remove-item {
        cursor: pointer;
        margin-left: 14px;
    }

    a:hover {
            color: red;
        }

</style>
