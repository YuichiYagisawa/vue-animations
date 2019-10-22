<template>
  <div class="home">
    <button @click="bounce = !bounce">Bounce</button><br>
    <section>
      <transition name="bounce">
        <img v-if="bounce" alt="Vue logo" src="../assets/logo.png">
      </transition>
    </section>
    <button @click="roll = !roll">Roll</button><br>
    <section>
      <transition name="roll">
        <img v-if="roll" alt="Vue logo" src="../assets/logo.png">
      </transition>
    </section>
    <button @click="animated = !animated">Animate</button><br>
    <section>
      <transition name="animate" enter-active-class="animated flipInY" leave-active-class="animated zoomOutRight">
        <img v-if="animated" alt="Vue logo" src="../assets/logo.png">
      </transition>
    </section>

    <div class="book">
      <div class="book__page"></div>
      <div class="book__page"></div>
      <div class="book__page"></div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'home',
  data() {
    return{
      bounce: false,
      roll: false,
      animated: false

    }
  }
}
</script>

<style lang="scss">


section {
  height: 200px;
}

.bounce-enter-active{
  animation: bounce-in .5s;
}

.bounce-leave-active{
  animation: bounce-in .5s reverse;
}

@keyframes bounce-in {
  0%{
    transform: scale(0);
  }
  50%{
    transform: scale(1.5);
  }
  100%{
    transform: scale(1);
  }
  
}

.roll-enter-active{
  animation: roll-in .5s;
}

.roll-leave-active{
  animation: roll-in .5s reverse;
}

@keyframes roll-in {
  0%{
    transform: scale(0) rotateZ(0deg) translate(-250px);
    opacity: 0;
  }
  50%{
    opacity: 1;
  }
  100%{
    transform: scale(1) rotateZ(360deg) translate(0px);
    opacity: 1;
  }
  
}


body{
  width:100%;
  height:100vh;
  background:#ffffff;
}
.book{
  top: 50%;
  transform: translateY(-50%);
  position:relative;
  margin:0 auto;
  border:5px solid #000000;
  width:100px;
  height:60px;
}
.book__page{
  position:absolute;
  left:50%;
  top:-5px;
  margin:0 auto;
  border-top:5px solid #000000;
  border-bottom:5px solid #000000;
  border-right:5px solid #000000;
  background: #ffffff;
  width:50px;
  height:60px;
  transform-origin:0% 50%;
  animation:flip 1.2s infinite linear;
  animation-fill-mode:forwards;
  
  @for $i from 1 through 3 {
    &:nth-child(#{$i}) { 
      z-index:-$i;
      animation-delay:1.4s*$i;
    }
  }
}

@keyframes flip {
  0%{
      transform: perspective( 600px )
      rotateY( -0deg );
  }
  
  20%{
    background:darken(#ffffff,10%);
  }
  
  29.9%{
      background:darken(#ffffff,10%);
  }
  30%{
      transform: perspective( 200px )
      rotateY( -90deg );
      background:#ffffff;
  }
  
  54.999%{
    opacity:1;
  }
  55%{
    opacity:0;
  }
  
  60%{
    transform: perspective( 200px )
    rotateY( -180deg );
    background:#ffffff;
  }
  
  100%{
    transform: perspective( 200px )
    rotateY( -180deg );
    background:#ffffff;
  }
}
</style>
