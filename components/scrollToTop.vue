<template>
  <div v-show="scY > 300" @click="toTop" class="container">
    <i class="fas fa-chevron-up"></i>
  </div>
</template>

<script>
export default {
  data() {
    return {
      scTimer: 0,
      scY: 0,
    };
  },
  methods: {
    handleScroll () {
        if (this.scTimer) return;
        this.scTimer = setTimeout(() => {
          this.scY = window.scrollY;
          clearTimeout(this.scTimer);
          this.scTimer = 0;
        }, 100);
      },
      toTop () {
        window.scrollTo({
          top: 0,
          behavior: "smooth"
        });
      },
  },
  mounted() {
      window.addEventListener("scroll", this.handleScroll)
  }
};
</script>

<style scoped>
.container {
  background: #04ed93;
  display: inline-block;
  position: fixed;
  bottom: 0;
  right: 0;
  transform: translate(-100%, -100%);
  width: 40px;
  height: 40px;
  border-radius: 50%;
  text-align: center;
  cursor: pointer;
  z-index: 10001;
  transition: all .4s ease;
}
.container i {
  color: #fff;
  transform: translateY(50%);
  z-index: 10002;
}

.container:hover {
  margin-bottom: 5px;
}

@media (max-width: 800px) {
    .container {
        bottom: 0;
        right: 0;
        transform: translate(-75%, -75%);
    }
}
</style>
