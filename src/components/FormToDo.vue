<template>
  <div class="form-todo form-group">
    <p>
      <input type="text" placeholder="Nome" name="author" class="form-control" v-model="name">
    </p>
    <p>
      <textarea name="message" placeholder="Comentário" class="form-control" v-model="message"></textarea>
    </p>
    <p>
      <button v-on:click.prevent="handleAddComment" type="submit" class="btn btn-primary">Comentar</button>
    </p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: '',
      message: ''
    }
  },

  methods: {
    handleAddComment() {
      if(this.message.trim() === '') {
        return
      }
      this.$emit('add-todo', {
        name: this.name,
        message: this.message,
      });
      this.name='';
      this.message='';
    },

  }
}
</script>