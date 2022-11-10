<script>
import { defineComponent } from 'vue';

export default /*#__PURE__*/defineComponent({
  name: "InfiniteScroll",
  props: {
    active: {
      type: Boolean,
      default: () => true
    },

    distance: {
      type: String,
      default: () => '200px'
    },

    autoLoad: {
      type: Boolean,
      default: () => false
    }
  },

  mounted() {
    if (this.autoLoad) {
      this.emitEvent();
    }

    this.observer();
  },

  methods: {
    emitEvent() {
      this.$emit('process')
    },

    observer() {
      const options = {
        rootMargin: '0px',
        threshold: 0
      }

      const callback = (entries) => {
        if (this.active && entries[0].isIntersecting) {
          this.emitEvent();
        }
      }

      const observer = new IntersectionObserver(callback, options);
      observer.observe(this.$refs.infiniteScrollObserver);
    }
  },

  computed: {
    getStyle() {
      return {
        marginBottom: '-' + this.distance,
        top: '-' + this.distance
      }
    }
  }
});
</script>

<template>
  <div class="infiniteScrollObserver" ref="infiniteScrollObserver" :style="getStyle"></div>
</template>

<style scoped>
  .infiniteScrollObserver {
    height: 5px;
    position: relative;
  }
</style>