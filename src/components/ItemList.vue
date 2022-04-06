<template id="item-list">
    <li class="tasks__item">
      <button :class="className"
          @click.self="$emit('complete')"
      >
        {{ task.title }}
      </button>
      <button class="tasks__item__remove button alert pull-right"
              @click="$emit('remove')"
      >
        <i class="fa fa-times"></i>
      </button>
    </li>
</template>
<script>

export default ('item-list',{
    name: 'ItemList',
    template: '#item-list',
    props: ['task'],
    computed: {
      className() {
        let classes = ['tasks__item__toggle'];
        if (this.task.completed) {
          console.log("in complete");
          classes.push('tasks__item__toggle--completed');
        }
        return classes.join(' ');
      }
    }
})
</script>
