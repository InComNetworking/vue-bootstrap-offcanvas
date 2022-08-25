<style lang="scss" scoped></style>
<template>
  <div
    class="offcanvas"
    :class="offcanvasClasses"
    
    :aria-hidden="isShow"
    :aria-modal="isShow"
    :style="customStyle"
    :role="getRole"
  >
    <div class="offcanvas-header">
      <slot name="header"></slot>
    </div>
    <div class="offcanvas-body">
      <slot name="body"></slot>
    </div>
    
  </div>
  <div
    v-if="isBackdrop"
    ref="root"
    class="offcanvas-backdrop"
    :class="backdropClasses"
    @click="cancelEvent"
  ></div>
</template>
<script>
var allowedOffcanvasPositions = ['start', 'end', 'top', 'bottom']
export default {
  data() {
    return {
      isShow: false,
    };
  },
  emits: ["hideBsOffcanvas"],
  props: ["placement", "data-bs-backdrop", "data-bs-scroll"],
  watch: {},
  computed: {
    isBackdrop: function(){
      if(this["data-bs-backdrop"] === false) {
        return false
      }
      return true
    },
    getRole: function(){
      if(this.isShow) {
        return "dialog"
      }
      return;
    },
    customStyle: function(){
      if(!this.isShow) {
        return "visibility: hidden;"
      }
      return 'visibility: visible';
    },
    offcanvasClasses: function(){
      var result = ["fade"];
      if (this.isShow) {
        result.push("show");
      }
      var placement = "start";
      if (this.placement 
        && allowedOffcanvasPositions.indexOf(this.placement) !== -1) {
        placement = this.placement
      }
      result.push("offcanvas-" + placement)
      return result.join(" ");
    },
    backdropClasses: function () {
      var result = ["fade"];
      if (this.isShow) {
        result.push("show");
      }
      return result.join(" ");
    },
  },
  methods: {
    processClick: function (callback) {
      this.isShow = false;
      setTimeout(function () {
        callback();
      }, 100);
    },
    closeEvent: function (e) {
      this.isShow = false;
      var self = this;
      setTimeout(function () {
        self.$emit("hideBsOffcanvas");
      }, 100);
    },
    cancelEvent: function (e) {
      if (this.$refs["root"] && this.$refs["root"] == e.target) {
        this.isShow = false;
        var self = this;
        setTimeout(function () {
          self.$emit("hideBsOffcanvas");
        }, 100);
      }
    },
  },
  mounted() {
    var self = this;
    setTimeout(function () {
      self.isShow = true;
    }, 100);
  },
};
</script>
