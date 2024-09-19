<template>
  <v-app>
    <v-main>
      <ToDoList/>
    </v-main>
  </v-app>
</template>

<script>
//import HelloWorld from './components/HelloWorld.vue'
import ToDoList from './components/ToDoList.vue';


export default {
  name: 'App',

  components: {
    ToDoList,
  },

  data: () => ({
    //
  }),
}
</script>