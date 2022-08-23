<template>
  <div :class="`task ${task.done ? 'is-complete' : ''}`">
    <div class="content">
      {{ task.content }}
    </div>
    <div class="buttons">
      <button @click="toggleDone">
        {{ task.done ? 'Desfazer' : 'Feito' }}
      </button>
      <button @click="removeTask" class="delete">
        Deletar
      </button>
    </div>
  </div>
</template>

<script>
export default {
  // eslint-disable-next-line vue/require-prop-types
  props: ['task'],
  methods: {
    toggleDone () {
      this.$store.commit('toggle_task', this.task)
    },
    removeTask () {
      this.$store.commit('remove_task', this.task)
    }
  }
}
</script>
