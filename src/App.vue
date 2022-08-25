<style lang="scss">
#app {
  padding: 2rem;
  font-weight: normal;
  width: 100%;
}

@media (min-width: 1024px) {
  body {
    display: flex;
    place-items: center;
  }
}
.root {
  position: relative;
  padding: 2em 0;
  margin-top: 2em;
  margin-bottom: 2em;
  border-bottom: 1px solid #ccc;
}
.root::before {
  content: "";
  position: absolute;
  top: 0;
  left: 18px;
  height: 100%;
  width: 2px;
  background: #d7e4ed;
}

@media (min-width: 992px) {
  .bd-sidebar {
    position: -webkit-sticky;
    position: sticky;
    top: 5rem;
    display: block !important;
    height: calc(100vh - 6rem);
    padding-left: 0.25rem;
    margin-left: -0.25rem;
    overflow-y: auto;
  }
}

@media (min-width: 992px) {
  .bd-layout {
    display: grid;
    grid-template-areas: "sidebar main";
    grid-template-columns: 1fr 4fr;
    gap: 0.5rem;
  }
}

@media (max-width: 991.98px) {
  .bd-main {
    max-width: 760px;
    margin-inline: auto;
  }
}

@media (min-width: 768px) {
  .bd-main {
    display: grid;
    grid-template-areas: "intro" "content";
    grid-template-rows: auto auto 1fr;
    gap: inherit;
  }
}

@media (min-width: 992px) {
  .bd-main {
    grid-template-areas: "intro" "content";
    grid-template-rows: auto 1fr;
  }
}
</style>
<template>
  <div class="container">
    <!-- Button trigger offcanvas -->
    <hr />
    <label>Enable default</label>
    <hr />
    <div class="btn-group">
      <button
        type="button"
        class="btn btn-primary"
        @click="showOffCanvas('start')"
      >
        Launch offcanvas start
      </button>
      <button
        type="button"
        class="btn btn-primary"
        @click="showOffCanvas('end')"
      >
        Launch offcanvas end
      </button>
      <button
        type="button"
        class="btn btn-primary"
        @click="showOffCanvas('top')"
      >
        Launch offcanvas top
      </button>
      <button
        type="button"
        class="btn btn-primary"
        @click="showOffCanvas('bottom')"
      >
        Launch offcanvas bottom
      </button>
    </div>
    <hr />
    <label>Enable no backdrop</label>
    <hr />
    <div class="btn-group">
      <button
        type="button"
        class="btn btn-primary"
        @click="showOffCanvas('start', false)"
      >
        Launch offcanvas start
      </button>
      <button
        type="button"
        class="btn btn-primary"
        @click="showOffCanvas('end', false)"
      >
        Launch offcanvas end
      </button>
      <button
        type="button"
        class="btn btn-primary"
        @click="showOffCanvas('top', false)"
      >
        Launch offcanvas top
      </button>
      <button
        type="button"
        class="btn btn-primary"
        @click="showOffCanvas('bottom', false)"
      >
        Launch offcanvas bottom
      </button>
    </div>
    <hr />
    <label>Enable no backdrop with scroll</label>
    <hr />
    <div class="btn-group">
      <button
        type="button"
        class="btn btn-primary"
        @click="showOffCanvas('start', false, true)"
      >
        Launch offcanvas start
      </button>
      <button
        type="button"
        class="btn btn-primary"
        @click="showOffCanvas('end', false, true)"
      >
        Launch offcanvas end
      </button>
      <button
        type="button"
        class="btn btn-primary"
        @click="showOffCanvas('top', false, true)"
      >
        Launch offcanvas top
      </button>
      <button
        type="button"
        class="btn btn-primary"
        @click="showOffCanvas('bottom', false, true)"
      >
        Launch offcanvas bottom
      </button>
    </div>
    {{ result }}
    {{ isOffCanvas }}
    <div style="padding: 100px 100px">
      Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Aenean commodo
      ligula eget dolor. Aenean massa. Cum sociis natoque penatibus et magnis
      dis parturient montes, nascetur ridiculus mus. Donec quam felis, ultricies
      nec, pellentesque eu, pretium quis, sem. Nulla consequat massa quis enim.
      Donec pede justo, fringilla vel, aliquet nec, vulputate eget, arcu. In
      enim justo, rhoncus ut, imperdiet a, venenatis vitae, justo. Nullam dictum
      felis eu pede mollis pretium. Integer tincidunt. Cras dapibus. Vivamus
      elementum semper nisi. Aenean vulputate eleifend tellus. Aenean leo
      ligula, porttitor eu, consequat vitae, eleifend ac, enim. Aliquam lorem
      ante, dapibus in, viverra quis, feugiat a, tellus. Phasellus viverra nulla
      ut metus varius laoreet. Quisque rutrum. Aenean imperdiet. Etiam ultricies
      nisi vel augue. Curabitur ullamcorper ultricies nisi. Nam eget dui. Etiam
      rhoncus. Maecenas tempus, tellus eget condimentum rhoncus, sem quam semper
      libero, sit amet adipiscing sem neque sed ipsum. Nam quam nunc, blandit
      vel, luctus pulvinar, hendrerit id, lorem. Maecenas nec odio et ante
      tincidunt tempus. Donec vitae sapien ut libero venenatis faucibus. Nullam
      quis ante. Etiam sit amet orci eget eros faucibus tincidunt. Duis leo. Sed
      fringilla mauris sit amet nibh. Donec sodales sagittis magna. Sed
      consequat, leo eget bibendum sodales, augue velit cursus nunc,
      <hr />
      Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Aenean commodo
      ligula eget dolor. Aenean massa. Cum sociis natoque penatibus et magnis
      dis parturient montes, nascetur ridiculus mus. Donec quam felis, ultricies
      nec, pellentesque eu, pretium quis, sem. Nulla consequat massa quis enim.
      Donec pede justo, fringilla vel, aliquet nec, vulputate eget, arcu. In
      enim justo, rhoncus ut, imperdiet a, venenatis vitae, justo. Nullam dictum
      felis eu pede mollis pretium. Integer tincidunt. Cras dapibus. Vivamus
      elementum semper nisi. Aenean vulputate eleifend tellus. Aenean leo
      ligula, porttitor eu, consequat vitae, eleifend ac, enim. Aliquam lorem
      ante, dapibus in, viverra quis, feugiat a, tellus. Phasellus viverra nulla
      ut metus varius laoreet. Quisque rutrum. Aenean imperdiet. Etiam ultricies
      nisi vel augue. Curabitur ullamcorper ultricies nisi. Nam eget dui. Etiam
      rhoncus. Maecenas tempus, tellus eget condimentum rhoncus, sem quam semper
      libero, sit amet adipiscing sem neque sed ipsum. Nam quam nunc, blandit
      vel, luctus pulvinar, hendrerit id, lorem. Maecenas nec odio et ante
      tincidunt tempus. Donec vitae sapien ut libero venenatis faucibus. Nullam
      quis ante. Etiam sit amet orci eget eros faucibus tincidunt. Duis leo. Sed
      fringilla mauris sit amet nibh. Donec sodales sagittis magna. Sed
      consequat, leo eget bibendum sodales, augue velit cursus nunc,
      <hr />
      Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Aenean commodo
      ligula eget dolor. Aenean massa. Cum sociis natoque penatibus et magnis
      dis parturient montes, nascetur ridiculus mus. Donec quam felis, ultricies
      nec, pellentesque eu, pretium quis, sem. Nulla consequat massa quis enim.
      Donec pede justo, fringilla vel, aliquet nec, vulputate eget, arcu. In
      enim justo, rhoncus ut, imperdiet a, venenatis vitae, justo. Nullam dictum
      felis eu pede mollis pretium. Integer tincidunt. Cras dapibus. Vivamus
      elementum semper nisi. Aenean vulputate eleifend tellus. Aenean leo
      ligula, porttitor eu, consequat vitae, eleifend ac, enim. Aliquam lorem
      ante, dapibus in, viverra quis, feugiat a, tellus. Phasellus viverra nulla
      ut metus varius laoreet. Quisque rutrum. Aenean imperdiet. Etiam ultricies
      nisi vel augue. Curabitur ullamcorper ultricies nisi. Nam eget dui. Etiam
      rhoncus. Maecenas tempus, tellus eget condimentum rhoncus, sem quam semper
      libero, sit amet adipiscing sem neque sed ipsum. Nam quam nunc, blandit
      vel, luctus pulvinar, hendrerit id, lorem. Maecenas nec odio et ante
      tincidunt tempus. Donec vitae sapien ut libero venenatis faucibus. Nullam
      quis ante. Etiam sit amet orci eget eros faucibus tincidunt. Duis leo. Sed
      fringilla mauris sit amet nibh. Donec sodales sagittis magna. Sed
      consequat, leo eget bibendum sodales, augue velit cursus nunc,
      <hr />
    </div>

    <!-- Offcanvas -->
    <OffcanvasView
      v-if="isOffCanvas"
      :placement="placement"
      @hide-bs-offcanvas="eventReceived"
      :data-bs-backdrop="DataBsBackdrop"
      :data-bs-scroll="DataBsScroll"
    >
      <template v-slot:header> here is header </template>
      <template v-slot:body>
        OffCanvas view status - <b>{{ isOffCanvas }}</b>
      </template>
    </OffcanvasView>
  </div>
</template>
<script>
export default {
  data() {
    var self = this;
    return {
      isOffCanvas: false,
      placement: "start",
      backdrop: true,
      scroll: false,
      result: "",
      actionSettings: [
        {
          title: "Cancel",
          class: "btn-secondary",
          click: function () {
            self.result = "Cancel clicked";
            self.isOffCanvas = false;
          },
        },
        {
          title: "Do Danger",
          class: "btn-danger",
          click: function () {
            self.result = "Danger clicked";
          },
        },
        {
          title: "Confirm",
          class: "btn-success",
          click: function () {
            self.result = "Confirm clicked";
          },
        },
      ],
    };
  },
  computed: {
    DataBsBackdrop: function () {
      if (this.backdrop === false) {
        return false;
      }
      return;
    },
    DataBsScroll: function () {
      if (this.scroll === true) {
        return true;
      }
      return;
    },
  },
  methods: {
    showOffCanvas: function (placement, backdrop, scroll) {
      this.placement = placement;
      this.isOffCanvas = true;
      console.log("backdrop", backdrop);
      this.backdrop = true;
      if (backdrop === false) {
        this.backdrop = false;
      }
      this.scroll = false;
      if (scroll === true) {
        this.scroll = true;
      }
    },
    eventReceived: function (e, type) {
      this.isOffCanvas = false;
    },
  },
  mounted() {},
};
</script>
