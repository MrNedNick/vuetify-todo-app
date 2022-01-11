<template>
    <div class="main"> 

        <h2>VUE TODO APP</h2>

        <div class="input__block">
            <input class="input" 
              @keyup.enter="submitTask" 
              v-model="task" type="text" 
              placeholder="Enter task">
            <v-btn
              color="secondary"
              elevation="2"
              large
              outlined
              @click="submitTask"
            >
              SUBMIT
            </v-btn>
        </div>

        <div class="list" v-for="(task, index) in tasks" :key='index'>
            <div class="list__item">
                <div class='item__name'>{{ task.name }}</div>
                <div class="item__edit">
                    <div class="edit__item" @click="editTask(index)">
                        <span class="fa fa-pen"></span>
                    </div>
                    <input 
                      class="edit__item" 
                      :value='index' type="checkbox" 
                      v-model="checked">
                    <div class="edit__item" @click="deleteTask(index)">
                        <span class="fa fa-trash"></span>
                    </div>
                </div>
            </div>
        </div>  
        <br>
        <div >
          <v-app id="inspire">
            <v-row justify="center">
              <v-dialog
                v-model="dialog"
                persistent
                max-width="290"
              >
                <template v-slot:activator="{ on, attrs }">
                  <v-btn
                    class="modal__btn"
                    color="primary"
                    dark
                    v-bind="attrs"
                    v-on="on"
                  >
                    DELETE
                  </v-btn>
                </template>
                <v-card>
                  <v-card-title class="text-h5">
                    Are you sure?
                  </v-card-title>
                  <v-card-actions>
                    <v-spacer></v-spacer>
                    <v-btn
                      color="green darken-1"
                      text
                      @click="dialog = false"
                    >
                      NO
                    </v-btn>
                    <v-btn
                      color="green darken-1"
                      text
                      @click="deleteSelected(index)"
                    >
                      YES
                    </v-btn>
                  </v-card-actions>
                </v-card>
              </v-dialog>
            </v-row>
          </v-app>
        </div>

    </div>
</template>

<script>
      
export default {
    data(){
        return {
            dialog: false,
            task: '',
            editedTask: null,
            checked: [],
            tasks: [
                {
                    name: 'Clean my room',
                },
                {
                    name: 'Read new book',
                }
            ]
        }
    },

    methods: {
        submitTask(){
            if(this.task.length === 0) return;

            if(this.editedTask === null){
                this.tasks.push({
                    name: this.task,
                    status: 'to-do'
                })
            }else{
                this.tasks[this.editedTask].name = this.task
                this.editedTask = null
            }

            this.task = ''
        },

        deleteTask(index){
            this.tasks.splice(index, 1)
        },

        deleteSelected(){
            this.checked.splice(0, this.checked.length)

            this.dialog = false
        },

        editTask(index){
            this.task = this.tasks[index].name
            this.editedTask = index
        }
    }
}


</script>

<style scoped>
  .main{
      display: flex;
      flex-direction: column;
      align-items: center;
      margin-top: 50px;
  }
  .input__block{
    margin: 30px 0;
  }
  .title {
    margin-top: 30px;
  }
  .input{
      height: 42px;
      width: 300px;
      padding: 10px;
  }
  .list__item {
      display: flex;
      justify-content: space-between;
      width: 400px;
      margin: 10px;
  }
  .item__edit {
      display: flex;
  }
  .edit__item{
      margin-right: 10px;
}
</style>
