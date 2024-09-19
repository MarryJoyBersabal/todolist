<template>
    <v-app>
      <v-container class="todo-container" fluid>
        <v-row class="justify-center align-center">
          <v-col cols="12" md="6" class="task-container">
            <!-- Input for adding new tasks -->
            <v-text-field
              v-model="newTask"
              label="Add a new task"
              @keyup.enter="addTask"
              outlined
              class="task-input"
            ></v-text-field>
            <v-btn
              @click="addTask"
              color="primary"
              :disabled="!newTask"
              class="add-task-btn"
            >
              Add Task
            </v-btn>
    
            <!-- List of tasks -->
            <v-list two-line>
              <v-list-item-group>
                <v-list-item
                  v-for="(task, index) in tasks"
                  :key="index"
                  class="task-item"
                >
                  <v-list-item-content>
                    <v-list-item-title>{{ task.title }}</v-list-item-title>
                    <v-list-item-subtitle>{{ task.date }}</v-list-item-subtitle>
                  </v-list-item-content>
                  <v-list-item-action>
                    <v-btn icon @click="deleteTask(index)" class="delete-btn">
                      <v-icon>mdi-delete</v-icon>
                    </v-btn>
                  </v-list-item-action>
                </v-list-item>
              </v-list-item-group>
            </v-list>
          </v-col>
        </v-row>
      </v-container>
    </v-app>
  </template>
  
  <script>
  export default {
    data() {
      return {
        newTask: "",
        tasks: [
          { title: "Complete Vue.js project", date: "2024-09-17" },
          { title: "Buy groceries", date: "2024-09-18" },
        ],
      };
    },
    methods: {
      addTask() {
        if (this.newTask) {
          this.tasks.push({
            title: this.newTask,
            date: new Date().toISOString().slice(0, 10), // current date
          });
          this.newTask = "";
        }
      },
      deleteTask(index) {
        this.tasks.splice(index, 1);
      },
    },
  };
  </script>
  
  <style scoped>
  
  .todo-container {
    background-image: url('https://s3.us-west-2.amazonaws.com/images.unsplash.com/small/photo-1664575602276-acd073f104c1');
    background-size: cover;
    background-position: center;
    min-height: 100vh;
    padding: 30px;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  
 
  .task-container {
    background-color: rgba(255, 255, 255, 0.9);
    border-radius: 12px;
    padding: 20px;
    box-shadow: 0px 4px 15px rgba(0, 0, 0, 0.1);
  }
  
  /* Style  button */
  .task-input {
    border-radius: 9px;
    padding: 8px;
  }
  
  .add-task-btn {
    margin-left: 10px;
    background-color: #0e0e14;
    color: white;
  }
  
  .add-task-btn:hover {
    background-color: #0c0b0c;
  }
  
  /* Style the list items */
  .task-item {
    background-color: rgba(230, 227, 223, 0.9);
    margin-bottom: 12px;
    border-radius: 10px;
    padding: 10px;
    box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.1); 
    transition: transform 0.2s, box-shadow 0.2s;
    display: flex;
    align-items: center; 
    justify-content: space-between; 
  }
  
  .task-item:hover {
    transform: translateY(-3px);
    box-shadow: 0px 6px 12px rgba(0, 0, 0, 0.2);
  }
  
  /* Task content styling */
  .task-content {
    flex: 1; 
  }
  
  /* Task action styling */
  .task-action {
    display: flex;
    align-items: center;
  }
  
  .v-list-item-title {
    font-size: 15px;
    font-weight: bold;
  }
  
  .v-list-item-subtitle {
    font-size: 14px;
    color: #6b6b6b;
  }
  
  /* Delete button styling */
  .delete-btn {
    color: #d9534f; 
  }
  </style>