<style lang="scss" scoped></style>
<template>
  <div
    class="offcanvas"
    :class="offcanvasClasses"
    :aria-hidden="!isShow"
    :aria-modal="isShow"
    :style="customStyle"
    :role="getRole"
  >
    <div class="offcanvas-header">
      <slot name="header"></slot>
      <h5 v-if="title" class="offcanvas-title">{{title}}</h5>
      <button
        v-if="btnClose"
        type="button"
        class="btn-close text-reset"
        data-bs-dismiss="offcanvas"
        aria-label="Close"
        @click="hide"
        ></button>
    </div>
    <div class="offcanvas-body">
      <slot name="body"></slot>
    </div>
  </div>
  <div
    @scroll="scrollEvent"
    @touchmove="scrollEvent"
    v-if="isBackdrop && isShow"
    ref="root"
    class="offcanvas-backdrop"
    :class="backdropClasses"
    @click="clickHide"
  ></div>
</template>
<script>
var allowedOffcanvasPositions = ["start", "end", "top", "bottom"];
export default {
  data() {
    return {
      isShow: false,
      customStyle: "visibility: hidden;",
    };
  },
  emits: ["hideBsOffcanvas","hiddenBsOffcanvas", "showBsOffcanvas", "shownBsOffcanvas"],
  props: ["placement", "dataBsBackdrop", "dataBsScroll", "btnClose", "title"],
  watch: {
    isShow: function (newValue) {
      if (newValue) {
        this.$emit("shownBsOffcanvas");
        if (this.dataBsScroll !== true) {
          this.disableScroll();
        }
        this.customStyle = "visibility: visible";
        return;
      }
      this.enableScroll();
      var self = this;
      setTimeout(function () {
        self.customStyle = "visibility: hidden;";
        self.$emit("hiddenBsOffcanvas");
      }, 500);
    },
  },
  computed: {
    isBackdrop: function () {
      if (this["dataBsBackdrop"] === false) {
        return false;
      }
      return true;
    },
    getRole: function () {
      if (this.isShow) {
        return "dialog";
      }
      return;
    },
    offcanvasClasses: function () {
      var result = [];
      if (this.isShow) {
        result.push("show");
      }
      var placement = "start";
      if (
        this.placement &&
        allowedOffcanvasPositions.indexOf(this.placement) !== -1
      ) {
        placement = this.placement;
      }
      result.push("offcanvas-" + placement);
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
    scrollEvent: function (e) {
      console.log("scroll", e);
    },
    clickHide: function (e) {
      if (this.$refs["root"] && this.$refs["root"] == e.target) {
        this.hide();
      }
    },
    hide: function () {
      this.isShow = false;
      var self = this;
      self.$emit("hideBsOffcanvas");

    },

    disableScroll: function () {
      document.body.style.overflow = "hidden";
    },
    enableScroll: function () {
      document.body.style.overflow = "";
    },
    show: function () {
      var self = this;
      setTimeout(function () {
        self.isShow = true;
        self.$emit("showBsOffcanvas");
      }, 100);
    },
  },
  mounted() {},
};
</script>
