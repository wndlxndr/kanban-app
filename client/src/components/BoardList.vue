<template>
       <div class="container mt-3">
        <div class="row">
          <!-- Task Board -->
          <div class="col-md-3 col-sm-6 mt-3" v-for="category in categories" :key="category.id">
            <div class="p-2 rounded task-header"><h5 class="text-center">{{ category.name }} </h5></div>
            <div class="p-1 container-overflow">
                <!-- Loop Task List -->

                <div class="card" v-for="data in filteredTask(category.name)" :key="data.id">
                  <tasklist 
                    :dataList="data"
                    @idDelete='deleteData'
                    @updateData='updateData'
                    @updateCategory='updateCategory'>
                  </tasklist>  
                </div>

            </div>
            <div class="rounded task-bottom mb-2">
              <button type="button" class="btn btn-add fas fa-plus" @click="showAdd(category.name)"><label class="ml-3">Add</label></button>
            </div>
             <!-- Form Add -->
             <div class="add-task-page" v-if="pageAdd === category.name">
              <form @submit.prevent="addTask(category.name)">
                <textarea v-model="createTask" class ="add-task" name="add-backlog"></textarea>
                <button type="submit" class="btn btn-add-task fas fa-check"><label class="ml-2">Add Task</label></button>
                <button type="button" @click.prevent="cancelButton" class="btn btn-cancel fas fa-times"><label class="ml-2">Cancel</label></button>
              </form>
            </div>
          </div>

        </div>
      </div>
</template>

<script>
export default {
  
}
</script>