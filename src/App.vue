<template>
  <div class="mb-5">
      <button @click="ToggleButtons" :class="buttonStyle">{{btnData}}</button>
  </div>
  <div v-if="isProfile"><UserProfile /></div>
  <div v-if="isForm"><FormData /></div>
</template>

<script>
import UserProfile from './components/UserProfile.vue'
import FormData from './components/FormData.vue'

export default {
  name: 'App',
  components: {
    UserProfile, FormData
  },
  data(){
    return {
      isProfile: true,
      isForm:  false,
      btnData: "Open Form",
      buttonStyle: "btn btn-primary"
    }
  },
  methods: {
    ToggleButtons(){
      this.isProfile = !this.isProfile
      this.isForm = !this.isForm
      if(this.isForm){
          this.btnData = "Open Get User"
          this.buttonStyle = "btn btn-dark"
      }
      else{
        this.btnData ="Open Form",
        this.buttonStyle = "btn btn-secondary"
      }
    },
  }
}
</script>

<style>
#app {
  width: 400px;
  height: 100vh;
  margin: auto;
  text-align: center;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
</style>
