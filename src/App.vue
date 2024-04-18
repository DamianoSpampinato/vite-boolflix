<script >

import AppContentContainer from "./components/AppContentContainer.vue";
import { store } from './store.js';
export default{
  components: {
    AppContentContainer
  },
  data(){
    return{
      
      store,

    }
  },
  methods: {
    
  }
}
</script>

<template>
<AppContentContainer></AppContentContainer>
</template>

<style lang="scss">
@use './style/generic';
</style>
