<template> 
  <div id="about">
    <transition> 
      <div v-show="loading">
        <div class="book">
          <div class="book__page"></div>
          <div class="book__page"></div>
          <div class="book__page"></div>
        </div>
      </div>
    </transition>
    
    <transition>
      <div v-show="loading2">
        <p class="line-1 anim-typewriter">Color Book Review</p>
      </div>
    </transition>

    <transition enter-active-class="animated fadeIn delay">
      <div v-show="!loading && !loading2">
        <h1>about</h1>
      </div>
    </transition>
  </div>
</template>

<script>
export default {
  el: "#about",
  data() {
    return{
      loading: true,
      loading2: false
    }
  },
  mounted() {
    setTimeout(() => {
      this.loading = false;
      this.loading2 = true;
      setTimeout(() => {
        this.loading2 = false;
      }, 3500);
    }, 6000);
  }
}
</script>

<style scope>
  html{
    min-height: 100%;
    overflow: hidden;
  }
  body{
    height: calc(100vh - 8em);
    padding: 4em;
    color: #000000; 
    background-color: #ffffff;  
  }
  .line-1{
      position: relative;
      top: 50%;  
      width: 24em;
      margin: 0 auto;
      border-right: 2px solid rgba(255,255,255,.75);
      font-size: 180%;
      text-align: center;
      white-space: nowrap;
      overflow: hidden;
      transform: translateY(-50%);    
  }

  /* Animation */
  .anim-typewriter{
    animation: typewriter 4s steps(44) 1s 1 normal both,
  blinkTextCursor 500ms steps(44) infinite normal;
  }
  @keyframes typewriter{
    from{width: 0;}
    to{width: 24em;}
  }
  @keyframes blinkTextCursor{
    from{border-right-color: rgba(255,255,255,.75);}
    to{border-right-color: transparent;}
  }


  /* .fade-enter-active, .fade-leave-active {
    transition: opacity .5s;
  }
  .fade-enter, .fade-leave-to {
    opacity: 0;
  } */


  .v-enter-active, .v-leave-active {
    transition: opacity .5s
    
  }

  .v-enter, .v-leave-to {
    opacity: 0
  }

  /* .delay {
    animation-delay: 6s;
  } */
</style>