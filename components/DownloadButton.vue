<template>
  <div>
    <div :class="display">
      <div
        v-for="(store, index) in downloadStores"
        :key="index"
        :class="`flex justify-end mt-1.5 ${setFontColor}`"
      >
        <button
          :class="`flex items-center pl-2 lg:pl-5 pr-3 py-2 mb-4 rounded-lg ${setBackgroundColor} ${extraStyling}`"
        >
          <lazy-image-loader
            :paths="`footer-icons/${store}store${setIconColor}.png`"
            imageStyles="mr-4 lg:mr-5"
            containerStyles=""
            :alt="`${store}store`"
          ></lazy-image-loader>
          <div>
            <p class="text-xs">Download on</p>
            <h4 class="text-base lg:text-lg">
              {{ store.replace(store[0], store[0].toUpperCase()) }} Store
            </h4>
          </div>
        </button>
      </div>
    </div>
  </div>
</template>

<script>
import footerData from "./databases/footer-db";

export default {
  props: ["background", "extraStyling", "display"],
  data() {
    return {
      downloadStores: footerData[5].downloadStores,
    };
  },
  computed: {
    setBackgroundColor() {
      if (this.background == "black") {
        return "dark";
      } else {
        return "light";
      }
    },

    setFontColor() {
      if (this.background == "black") {
        return "text-white";
      } else {
        return "text-white";
      }
    },

    setIconColor() {
      if (this.background == "black") {
        return 1;
      } else {
        return 2;
      }
    },
  },
};
</script>

<style scoped>
.dark {
  background-color: #202223;
}

.light {
  background-color: #fff;
}
</style>
