<template>
  <q-layout view="lhh Lpr lFf">
    <q-header >
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="toggleLeftDrawer"
        />
      </q-toolbar>
      <div class="q-px-lg q-pt-xl q-mb-md">
        <div class="text-h3">Todo
          
        </div>
        <div class="text-subtitle">{{ todaysDate}}</div>
      </div>
      <img src="#" class="header-image" />
    </q-header>
    <q-drawer
        v-model="leftDrawerOpen"
        show-if-above
        :width="250"
        :breakpoint="600"
      >
        <q-scroll-area style="height: calc(100% - 192px); margin-top: 192px; border-right: 1px solid #ddd">
          <q-list padding>
            <q-item 
            to="/" 
            exact 
            clickable v-ripple>
              <q-item-section avatar>
                <q-icon name="list" />
              </q-item-section>

              <q-item-section>
                Todo
              </q-item-section>
            </q-item>
            <q-item to="/help" 
            exact 
            clickable v-ripple>
              <q-item-section avatar>
                <q-icon name="help" />
              </q-item-section>

              <q-item-section>
                Help
              </q-item-section>
            </q-item>

            </q-list>
</q-scroll-area>
        <q-img class="absolute-top" src="#" style="height: 192px">
          <div class="absolute-bottom bg-transparent">
            <q-avatar size="56px" class="q-mb-sm">
              <img src="#">
            </q-avatar>
            <div class="text-weight-bold">Rageena Filange</div>
            <div>@rara_Lang</div>
          </div>
        </q-img>
      </q-drawer>

    <q-page-container>
      <keep-alive>
        <router-view />
      </keep-alive>
      
    </q-page-container>
  </q-layout>
</template>

<script>
import { date } from 'quasar'
export default {
  name: 'MainLayout',
 
  data () {
    return {
      leftDrawerOpen: false
    }
  },
  computed:{
    todaysDate(){
      let timeStamp = Date.now()
      return date.formatDate(timeStamp, 'ddd D MMM YYYY')
    }
  }
}
</script>

<style lang="scss">
.header-image{
  height:100%;
  z-index:-1;
  opacity:0.2;
  filter: grayscale(100%);

}
</style>
