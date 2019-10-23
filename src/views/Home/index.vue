<template>
  <main id="app">
    <Board />
    <section id="feedbacks">
      <Feedback
        v-for="turn in total"
        v-bind:class="{ active: isActive(total - turn) }"
        v-bind:key="total - turn + 1"
        v-bind:fb="feedback[total - turn + 1]"
      />
    </section>
    <Check v-bind:style="{ transform: checkButtonTranslation }" />
    <Dialog v-if="won" status="happy" />
    <Dialog v-if="lost" status="sad" />
  </main>
</template>

<script>
import { mapGetters, mapState, mapActions } from "vuex";

import Board from "../../components/Board.vue";
import Feedback from "../../components/Feedback.vue";
import Check from "../../components/Check.vue";
import Dialog from "../../components/Dialog.vue";

export default {
  name: "app",
  components: {
    Board,
    Feedback,
    Check,
    Dialog
  },
  computed: {
    ...mapGetters(["checkButtonTranslation", "isActive"]),
    ...mapState(["current", "total", "won", "lost", "feedback"])
  },
  methods: {
    ...mapActions(["generateSecret"])
  },
  mounted() {
    this.generateSecret();
  }
};
</script>

<style lang="scss">
@import "../../assets/scss/reset";
@import "../../assets/scss/settings";
@import "../../assets/scss/utils";
@import "../../assets/scss/main";

#app {
  z-index: 1;
  padding-bottom: 30px;
}

#board {
  display: inline-block;
}

#feedbacks {
  @include main-shadow;
  background-color: $sand;
  border-radius: 0 $bd $bd 0;
  padding-bottom: $aria;
  z-index: -1;
  width: 75px;
  display: inline-block;
  position: absolute;
  top: 138px;
  margin-left: -15px;
}
</style>
