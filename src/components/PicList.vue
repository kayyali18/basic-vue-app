<template>
<section id="pic-list">
<transition v-if="show" name="fade">
  <Picture class="picture" v-bind:data='pic'></Picture>
</transition>
</section>

</template>


<script>
import Picture from './Picture'

export default {
  name: 'PicList',
  props: {
    pic: Object,
    msg: String,
    show: Boolean,
  },
  components: {
    Picture,
  },
}
</script>
  
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#pic-list {
  height: 200px;
  margin: 2rem;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}
</style>