<template>
  <section class="float-button-section" :class="[visible ? 'fade-in' : 'fade-out']">
    <div class="float-button">
      <span> <i class="icon iconfont icon-email"></i></span>
    </div>
  </section>
</template>

<script>
export default {
  name: 'ReplyFloatButton',

  data () {
    return {
      visible: true
    };
  },

  mounted() {
    let timer = null;
    window.addEventListener('scroll', () => {
      if (timer) {
        clearTimeout(timer);
      }
      timer = setTimeout(() => {
        this.visible = true;
      }, 300);
      if (this.visible) {
        this.visible = false;
      }
    });
  }
}
</script>
<style scoped>
.fade-in {
    animation-name: fade-in;
    animation-duration: 0.3s;
    animation-fill-mode: forwards;
}

.fade-out {
    animation-name: fade-out;
    animation-duration: 0.3s;
    animation-fill-mode: forwards;
}

@keyframes fade-in {
    0%   { opacity: 0; bottom: 3rem; }
    100% { opacity: 1; bottom: 4rem; }
}

@keyframes fade-out {
    0%   { opacity: 1; bottom: 4rem; }
    100% { opacity: 0; bottom: 3rem;}
}

.float-button-section {
    width: 4rem;
    height: 4rem;
    border-radius: 50%;
    background: #00d1b2;
    position: fixed;
    bottom: 4rem;
    right: 2rem;
    box-shadow: 0px 2px 5px #666;
}

.float-button span {
  color: white;
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;

  display: flex;
  justify-content: center;
  align-items: center;

  padding: 0;
  margin: 0;
}
.float-button span .icon {
    font-size: 24px;
    line-height: 55px;
    font-weight: 300;
}
</style>
