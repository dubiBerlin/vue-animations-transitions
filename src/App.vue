<template>
  <div class="container">
    <div class="row">
      <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
        <h1>Animations</h1>
        <hr>
        <button class="btn btn-primary" @click="show=!show">Show alert</button>
        <transition name="fade">
          <div class="alert alert-info" v-if="show">This is some info</div>
        </transition>
        <transition name="slide">
          <div class="alert alert-info" v-if="show">This is some info</div>
        </transition>
      </div>
    </div>
  </div>
</template>

<script>
import Test from "./components/Test.vue";

export default {
  name: "app",
  data() {
    return {
      show: false
    };
  },
  components: {
    appTest: Test
  }
};
</script>

<style>
.fade-enter {
  opacity: 0;
}

.fade-enter-active {
  transition: opacity 1s;
}

.fade-leave {
  opacity: 1;
}
.fade-leave-active {
  transition: opacity 1s;
  opacity: 0;
}
/**** slide ****/
.slide-enter {
}

/** forwards = dadurch bleibt das animierte Element an der Zielposition stehen und
               geht nicht zurück an den start. ***/
.slide-enter-active {
  animation: slide-in 1s ease-out forwards;
}

.slide-leave {
}
.slide-leave-active {
  animation: slide-out 1s ease-out;
}

@keyframes slide-in {
  from {
    transform: translateY(20px);
  }
  to {
    transform: translateY(0);
  }
}

@keyframes slide-out {
  from {
    transform: translateY(0);
  }
  to {
    transform: translateY(20px);
  }
}
</style>
