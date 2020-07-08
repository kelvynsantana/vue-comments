<template>
  <div class="container">
    <h1>Comentários</h1>
    <hr />

    <FormToDo v-on:add-todo="handleAddComment"/>
    <div class="list-group">
      <p v-if="comments.length <= 0">Sem comentários ainda 😭</p>
      <div class="list-group-item" v-bind:key="index" v-for="(comment, index) in allComments">
        <span class="comment_author">Autor: <strong>{{ comment.name }}</strong></span>
        <p>{{ comment.message }}</p>
        <div>
          <a href="#" title="Excluir" v-on:click.prevent="handleRemoveComment(index)">Excluir</a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import FormToDo from './FormToDo'
export default {
  components: {
    FormToDo,
  },
  data() {
      return {
        comments: [],

      }
    },
    methods: {
      handleAddComment(comment) {
        this.comments.push(comment);
      },

      handleRemoveComment(index) {
        this.comments.splice(index, 1);
      },
    },
    computed: {
      allComments() {
        return this.comments.map(comment => ({
          ...comment,
          name: comment.name.trim() === '' ? 'Anônimo' : comment.name
        }))
      },

    },

}
</script>
