<template>
  <section class="home position-relative">
    <div class="position-icon">
      <div class="chat-icon position-relative rounded-circle">
        <button @click=" popup = !popup" class="btn position-absolute top-50 start-50 translate-middle text-capitalize fw-semibold fs-5"><font-awesome-icon icon="headset"/></button>
      </div>
    </div>
    <div class="cont position-fixed top-0 start-50 translate-middle-x">
      <vue-particles color="#4c4a58" :particleOpacity="0.7" :particlesNumber="120" shapeType="circle"
        linesColor="#dfabdc" :moveSpeed="2" hoverMode="repulse"></vue-particles>
    </div>
    <div class="container">
      <div class="row mt-4 h-100">
        <div class="col-lg-7 col-md-6 col-12 d-flex flex-column align-items-center justify-content-center">
          <transition name="fade">
            <div v-if="popup">
            </div>
            <div v-else>
              <LeftSide :class="{ none: popup }"/>
            </div>
          </transition>
          <transition name="slide-fade">
            <div v-if="popup">
              <Robot :class="{ dis: popup }"/>
            </div>
          </transition>
        </div>
        <div class="col-lg-5 col-md-6 col-12 d-flex flex-column justify-content-center align-items-center">
          <transition name="slide-fade">
            <div v-if="popup">
              <div :class="{ dis: popup }">
                <ChatBot/>
              </div>
            </div>
          </transition>
          <transition name="fade">
            <div v-if="popup">
            </div>
            <div v-else>
              <Robot :class="{ none: popup }"/>
            </div>
          </transition>
          
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import Robot from '@/components/Home/Robot.vue'
import LeftSide from '@/components/Home/LeftSide.vue'
import ChatBot from '@/components/Chat/ChatBot.vue'

export default {
  name: 'Home',
  components: {
    Robot,
    LeftSide,
    ChatBot
  },
  data() {
    return {
      popup: false
    }
  },
  methods: {
    toggle: function(event, className) {
      event.target.classList.toggle(className)
    }
  },
  created () {
    GetData.apiChat()
    .then(response => {
      this.home = response.data
    })
    .catch(error => {
      console.log( `There was an error: ${error.response}`);
    })
  },
}
</script>

<style lang="scss" scoped>
@import '../sass/global/variables';
@import '../sass/global/animation';

.none {
  display: none;
  transition: $main-transition;
}
.dis {
  display: block;
}
.cont {
  height: 100%;
  max-height: 90vh;
  width: 100%;
  max-width: 100vw;
  z-index: -1;
}
.home {
  max-height: 95vh;

  .position-icon {
    position: fixed;
    right: 1%;
    bottom: 3%;
    z-index: 1000;
    .chat-icon {
      width: 3rem;
      height: 3rem;
      background: $second-main-color;
      border:  0.1rem dashed $main-color ;
    }
  }
}
</style>