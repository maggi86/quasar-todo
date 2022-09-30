<template>
  <q-page class="bg-green-1 container" padding>
    <!-- <div class="row q-pa-sm"> -->
    <q-input color="secondary" v-model="newTask" @keyup.enter="addTask" label="Add To List" dense>
      <q-btn flat style="color: green" label="Add" />
    </q-input>
      <!-- </div> -->
    <div class="q-pa-md">
    <div class="q-gutter-sm">
    <q-list class="bg-white" separator>
      <!--
        Rendering a <label> tag (notice tag="label")
        so QCheckboxes will respond to clicks on QItems to
        change Toggle state.
      -->

      <q-item
      v-for="(task, index) in tasks" 
      :key="task.title"
      @click="task.done = !task.done"
      :class="{ 'done' : task.done}"
      tag="label"
      clickable v-ripple>
        <q-item-section avatar>
          <q-checkbox 
          keep-color 
          v-model="task.done" 
          class="no-pointer-events"
          color="secondary" />
        </q-item-section>
        <q-item-section>
          <q-item-label>{{task.title}}</q-item-label>
        </q-item-section>
        <q-item-section
        v-if="task.done"
        side>
        <q-btn flat round 
        @click="task.stop"
        dense
        color="secondary" icon="delete" />

        </q-item-section>
      </q-item>

    </q-list>
    <div 
    v-if="!tasks.length"
    class="no-tasks absolute-center">
  <q-icon 
  name="check"
  size="100px"
  color="secondary"/>
  <div class="text-h5 text-secondary text-center">
    No Tasks
  </div>
  </div>
  </div>
  </div>
  </q-page>
</template>

<script>
import { ref } from 'vue'

export default{
  data() {
    return {
      tasks: [],
      newTask:''
    }
  },
  setup () {
    const secondary = ref(true)

    return {
      secondary,

      resetModels () {
        secondary.value = null
      }
    }
  },
  methods:{
    addTask(){
      this.tasks.push({
        title:this.newTask,
        done:true
      })
      this.newTask = ''
    },
    deleteTask(index){
      this.$q.dialog({
        title: 'confirm',
        message: 'Really You Wanna Delete?',
        cancel:true,
        persistent:true
      }).onOk(() => {
        this.tasks.splice(index,1)
      })
    },
    newTask(){


    }
      
    }
  }

</script>
