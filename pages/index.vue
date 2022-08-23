<template>
  <main>
    <h1>Quadro de Tarefas</h1>
    <p>Crie uma lista de tarefas</p>

    <div class="create-new">
      <input
        v-model="newTask"
        type="text"
        placeholder="Add uma nova tarefa"
        @keypress.enter="addTask"
      >
      <button @click="addTask">
        Add
      </button>
    </div>

    <div class="tasks">
      <task-component v-for="(task, i) in $store.state.tasks" :key="i" :task="task" />
    </div>
  </main>
</template>

<script>
export default {
  name: 'IndexPage',
  data () {
    return {
      newTask: ''
    }
  },
  methods: {
    addTask () {
      if (this.newTask) {
        this.$store.commit('add_task', this.newTask)
        this.newTask = ''
      }
    }
  }
}
</script>
