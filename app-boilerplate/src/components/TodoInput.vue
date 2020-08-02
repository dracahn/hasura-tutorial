<template>
  <div class="formInput">
    <input 
	class="input" 
	placeholder="What needs to be done?" 
	v-model="newTodo"
	@keyup.enter="addTodo"
    />
    <i class="downArrow fa fa-angle-right" />
  </div>
</template>

<script>
 import gql from "graphql-tag";

 const ADD_TODO = gql`
   mutation insert_todos($todo: String!, $isPublic: Boolean!) {
     insert_todos(objects: {title: $todo, is_public: $isPublic}) {
       affected_rows
       returning {
         id
         title
         is_completed
         created_at
         is_public
       }
     }
   }
 `;
  export default {
    props: ['type'],
    data() {
      return {
        newTodo: '',
      }
    },
    methods: {
      addTodo: function () {
        // insert new todo into db
      },
    }
  }
</script>
