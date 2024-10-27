<template>
  <div class="switcher">
    <div class="switch" @click="() => toggleTheme()">
      <div class="toggle" :class="toggleClass">
        <img
          v-if="showMoon"
          class="toggle__image"
          src="https://img.icons8.com/tiny-color/32/bright-moon.png"
          alt="Луна"
        />
        <img
          v-if="showSun"
          class="toggle__image"
          src="https://img.icons8.com/ultraviolet/32/sun--v1.png"
          alt="Солнце"
        />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ThemeSwiper",
  created() {
    const savedTheme = localStorage.getItem("theme");
    if (savedTheme) {
      this.isDarkMode = savedTheme === "dark";
      this.position = savedTheme === "dark" ? "right" : "left";
    } else {
      this.position = "center";
    }
  },
  data() {
    return {
      isDarkMode: false,
      position: "center",
    };
  },
  computed: {
    toggleClass() {
      return {
        "toggle--left": this.position === "left",
        "toggle--center": this.position === "center",
        "toggle--right": this.position === "right",
      };
    },
    showMoon() {
      return this.position === "right";
    },
    showSun() {
      return this.position === "left";
    },
  },
  methods: {
    toggleTheme() {
      if (this.position === "center") {
        this.position = "right";
        this.isDarkMode = true;
      } else if (this.position === "right") {
        this.position = "left";
        this.isDarkMode = false;
      } else {
        this.position = "right";
        this.isDarkMode = true;
      }
      localStorage.setItem("theme", this.isDarkMode ? "dark" : "light");
    },
  },
};
</script>

<style lang="less" scoped>
 @import 'styles/styles.less';
</style>