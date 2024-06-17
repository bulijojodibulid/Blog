<template>
  <div class="mouse-container">
    <div class="mouse-point" ref="mouse-point"></div>
    <div class="mouse-point-border" ref="mouse-point-border">
      <div class="mouse-point-expand" ref="mouse-point-expand"></div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Mouse",
  mounted() {
    window.onmousemove = (e) => {
      this.$refs['mouse-point'].style.transform = `translate(${e.pageX - 12}px, ${
        e.pageY - 12
      }px)`;
      this.$refs['mouse-point-border'].style.transform = `translate(${e.pageX}px, ${e.pageY}px)`;
    };

    window.onmouseover = (e) => {
      if (!!e.target.dataset.mousePointExpand) {
        this.$refs['mouse-point-expand'].style.width = "75px";
        this.$refs['mouse-point-expand'].style.height = "75px";
        this.$refs['mouse-point-border'].style.borderColor = "transparent";
      } else {
        this.$refs['mouse-point-expand'].style.width = "0";
        this.$refs['mouse-point-expand'].style.height = "0";
        this.$refs['mouse-point-border'].style.removeProperty("border-color");
      }
    };
  },
  destroyed(){
    window.onmousemove = null
    window.onmouseover = null
  }
};
</script>

<style lang="less" scoped>
.mouse-container{
    position: absolute;
}
.mouse-point {
  width: 8px;
  height: 8px;
  background-color: rgb(165, 166, 255);
  border-radius: 50%;
  position: absolute;
  z-index: 99;
  pointer-events: none;
  left: 8px;
  top: 8px;
}

.mouse-point-border {
  border: 2px solid rgb(165, 166, 255);
  width: 28px;
  height: 28px;
  background-color: transparent;
  border-radius: 50%;
  position: absolute;
  left: -14px;
  top: -14px;
  transition: 0.3s;
  z-index: 99;
  transition-timing-function: cubic-bezier(0.16, 0.84, 0.44, 1);
  pointer-events: none;
  display: flex;
  justify-content: center;
  align-items: center;
}

.mouse-point-expand {
  background-color: rgba(165, 166, 255, 0.5);
  border-radius: 50%;
  width: 0;
  height: 0;
  transition: 0.3s;
  flex-shrink: 0; /*当子元素宽度超过父元素时，子元素不压缩*/
}
</style>