<template>
  <q-page class="bg-green-1 column" padding>
    <q-input color="secondary" v-model="text" label="Add To List">
      </q-input>
    <div class="q-pa-md">
    <div class="q-gutter-sm">
    <q-list>
      <!--
        Rendering a <label> tag (notice tag="label")
        so QCheckboxes will respond to clicks on QItems to
        change Toggle state.
      -->

      <q-item
      v-for="task in tasks" 
      :key="task.title"
      tag="label" v-ripple>
        <q-item-section avatar>
          <q-checkbox 
          keep-color 
          v-model="task.done" color="secondary" />
        </q-item-section>
        <q-item-section>
          <q-item-label>{{task.title}}</q-item-label>
        </q-item-section>
      </q-item>

    </q-list>
  </div>
  </div>
  </q-page>
</template>

<script>
import { ref } from 'vue'

export default{
  data() {
    return {
      tasks: [
        {
        title : 'bananana',
        done:false
      }]
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
  }
}
</script>
