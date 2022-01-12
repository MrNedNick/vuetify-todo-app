<template>
  <v-container>
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
                    v-show="isShown()"
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
                      @click="deleteSelected()"
                    >
                      YES
                    </v-btn>
                  </v-card-actions>
                </v-card>
              </v-dialog>
            </v-row>
          </v-app>

  </v-container>
</template>

<script>
export default {
    name: 'Delete',
    data(){
        return {
            dialog: false,
            task: '',
            editedTask: null,
            isChecked: true,
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
        },
        isShown(){
          return true
          // if (this.checked.length > 0) {
          //   return true
          // } else {
          //   return false}
        }
    }
}


</script>


