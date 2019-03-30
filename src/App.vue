<template>
  <div class="container">
    <div class="row">
      <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
        <h1>Animations</h1>
        <hr>
        <hr>
        <button class="btn btn-primary" @click="show=!show">Show alert</button>
        <transition name="fade">
          <div class="alert alert-info" v-if="show">This is some info</div>
        </transition>
        <transition name="slide" type="animation">
          <div class="alert alert-info" v-if="show">This is some info</div>
        </transition>
        <transition name="fade" appear>
          <div class="alert alert-info" v-if="show">This is some info</div>
        </transition>
      </div>
    </div>
    <div class="row">
      <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
        <transition name="fade" appear>
          <div class="box" :style="{width: number+'%'}">
            <span style="margin-left: 15px; margin-top: 17px;">div</span>
          </div>
        </transition>
      </div>
    </div>
    <div class="row">
      <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
        <svg xmlns="http://www.w3.org/2000/svg" width="100%" height="100" id="chart">
          <g>
            <rect class="graph" height="30px" :width="number2 + '%'"></rect>
            <text y="17" x="15">svg</text>
          </g>
          <g>
            <rect class="graph2" y="30" height="30px" :width="number3 + '%'"></rect>
            <text y="17" x="15">svg</text>
          </g>
        </svg>
      </div>
    </div>
    <div class="row">
      <div class="col-xs-6 col-sm-4 col-sm-offset-1 col-md-3 col-md-offset-3">
        <button
          class="btn btn-primary"
          @click="number< 100 ?[number=number+getRandom(10),number2=number2+getRandom(10),number3=number3+getRandom(10)] : number=number"
        >ADD</button>
      </div>
      <div class="col-xs-6 col-sm-4 col-sm-offset-1 col-md-3 col-md-offset-3">
        <button
          class="btn btn-primary"
          @click="number > 0 ? [number=number-getRandom(10),number2=number2-getRandom(10),number3=number3-getRandom(10)] : number=number"
        >SUB</button>
      </div>
    </div>
    <div class="row">
      <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
        <button class="btn btn-primary" @click="getData()">Get data</button>
      </div>
      <div
        class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3"
      >{{number}}% {{number2}}% {{number3}}%</div>
    </div>
    <div class="row">
      <div class="col-12">
        <hr>
      </div>
    </div>

    <div class="row">
      <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
        <svg xmlns="http://www.w3.org/2000/svg" width="100%" height="400" id="chart">
          <circle r="5" cx="20" cy="20"></circle>
        </svg>
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
      show: true,
      number: 0,
      number2: 0,
      number3: 0
    };
  },

  methods: {
    getRandom(value) {
      return Math.floor(Math.random() * value) + 1;
    },
    getData(index, width) {
      this.number = this.getRandom(100);
      this.number2 = this.getRandom(100);
      this.number3 = this.getRandom(100);
    }
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
  opacity: 0;
}

/** forwards = dadurch bleibt das animierte Element an der Zielposition stehen und
               geht nicht zurück an den start. ***/
.slide-enter-active {
  animation: slide-in 1s ease-out forwards;
  transition: opacity 0.5s;
}

.slide-leave {
}
.slide-leave-active {
  animation: slide-out 1s ease-out;
  transition: opacity 8s;
  opacity: 0;
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

/**** animate width *****/
.box {
  height: 30px;
  width: 10px;
  background-color: red;
  transition-property: width;
  transition-duration: 1s;
}

.graph {
  fill: cornflowerblue;
  transition: width 0.5s;
}
.graph2 {
  fill: lightgreen;
  transition: width 0.5s;
}
</style>
