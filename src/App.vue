<template>
  <div>
    <TestList :tasks="tasks" />
    <ItemList />
  </div>
</template>

<script>
import TestList from './components/TestList.vue'
import ItemList from './components/ItemList.vue'

export default ({
  name: "app",
  components: {TestList, ItemList},
  data() {
    return {
      tasks: [
        {
          title: 'Make todo list',
          completed: true
        },
        {
          title: 'Go skydiving',
          completed: false
        }
      ]
    }
  }
})
</script>



<style>
/* #app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
} */

body {
  background-color: #abc;
}
*,
h1,
button {
  font-family: 'Nunito', sans-serif;
}
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}
.fade-enter,
.fade-leave-active {
  opacity: 0;
}
.tasks {
  width: 100%;
  max-width: 45rem;
  padding: 1em;
  margin: 1em auto;
  overflow: auto;
  background-color: #fff;
  box-shadow: 0px 0.25rem 1rem rgba(0,0,0,0.25);
}
.tasks__list {
  clear: both;
}
.tasks__item {
  margin-bottom: 0.5em;
  position: relative;
}
.tasks__item__toggle {
  cursor: pointer;
  width: 100%;
  text-align: left;
  padding: 0.85em 2.25em 0.85em 1em;
  background-color: rgba(0,0,0,0.05);
  border: 1px solid rgba(0,0,0,0.1);
}
.tasks__item__toggle:hover {
  background-color: rgba(0,0,0,0.1);
  border-color: rgba(0,0,0,0.15);
}
.tasks__item__toggle--completed {
  text-decoration: line-through;
  background-color: rgba(0,128,0,0.15);
  border-color: rgba(0,128,0,0.2);
}
.tasks__item__toggle--completed:hover {
  background-color: rgba(0,128,0,0.25);
  border-color: rgba(0,128,0,0.3);
}
.tasks__item__remove {
  position: absolute;
  height: 100%;
  top: 50%;
  right: 0;
  transform: translateY(-50%);
}
.tasks__item__remove i {
  vertical-align: middle;
}

</style>
