<template id="task-list">
    <section class="tasks">
      <h1>
        Tasks 
        <transition name="fade">
          <small v-if="incomplete">({{ incomplete }})</small>
        </transition>
        
      </h1>
      <div class="tasks__new input-group">
        <input type="text"
               class="input-group-field"
               v-model="newTask"
               @keyup.enter="addTask"
               placeholder="New task"
        >
        <span class="input-group-button">
          <button @click="addTask" 
                  class="button"
          >
            <i class="fa fa-plus"></i> Add
          </button>
        </span>
      </div>

      <div class="tasks__clear button-group pull-right">
        <button class="button warning small"
                @click="clearCompleted"
        >
          <i class="fa fa-check"></i> Clear Completed
        </button>
        <button class="button alert small"
                @click="clearAll"
        >
          <i class="fa fa-trash"></i> Clear All
        </button>
      </div>
      
      <transition-group name="fade" tag="ul" class="tasks__list no-bullet">
          <ItemList v-for="(task, index) in tasks"
                     @remove="removeTask(index)"
                     @complete="completeTask(task)"
                     @dragover="(e) => onDragOver(item, index, e)" 
                     @dragend="(e) => finishDrag(item, i, e)"
                     @dragstart="(e) => startDrag(item, i, e)"
                     :task="task"
                     :key="task"
          />
      </transition-group>
    </section>
</template>

<script>

import ItemList from './ItemList.vue'

export default ('task-list',{
    name: 'TestList',
    template: '#task-list',
    components: { ItemList },
    props: ['tasks'],
    data() {
        return {
            newTask: '',
        };
    },
    computed: {
        incomplete() {
            return this.tasks.filter(this.inProgress).length;
        }
    },
    methods: {
      addTask() {
        if (this.newTask) {
          this.tasks.push({
            title: this.newTask,
            completed: false
          });
          this.newTask = '';
        }
      },
      completeTask(task) {
        console.log(task);
        task.completed = !task.completed;
      },
      removeTask(index) {
        this.tasks.splice(index, 1);
      },

      clearCompleted() {
        console.log(this.tasks);
        console.log(this.tasks.filter(this.inProgress));
        this.tasks = this.tasks.filter(this.inProgress);
        console.log(this.tasks);
      },
      clearAll() {
        this.tasks = [];
      },
      
      inProgress(task) {
      console.log(!this.isCompleted(task));
        return !this.isCompleted(task);
      },
      isCompleted(task) {
        return task.completed;
    }
  }
})
</script>
