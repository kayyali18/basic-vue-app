<template>
<article id="picture">

  <figcaption>{{data.title}}</figcaption>
  <img v-bind:src="data.url" v-bind:alt="data.title" v-on:click="modal = !modal"/>
  <time v-bind:datetime="data.date">{{data.date}}</time>

  <transition name="fade">
    <div 
    class="modal" 
    v-if="modal"
    v-on:click="modal = !modal"
    >
      <img v-bind:src="data.url" v-bind:alt="data.title"  class="modal-img"/> 
    </div>
  </transition>

</article>

</template>
  
  <script>
export default {
  name: 'Picture',
  data() {
    return {
      modal: false,
    }
  },
  props: {
    data: Object,
    url: String,
  },
}
</script>
  
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#picture {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.modal {
  position: absolute;

  height: 70vh;
  /* width: 60vw; */
  border: 10px solid black;
  z-index: 33;
}

img {
  max-width: 200px;
}

.modal img {
  max-width: 60vw;
  max-height: 70vh;
}
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}
</style>