<template>
  <div class="switcher">
    <div class="switch" @click="() => toggleTheme()">
      <div class="toggle" :class="{ 'toggle--toggled': isDarkMode }">
        <img
          v-if="isDarkMode"
          class="toggle__image"
          src="https://img.icons8.com/tiny-color/32/bright-moon.png"
          alt="луна"/>
        <img
          v-else
          class="toggle__image"
          src="https://img.icons8.com/ultraviolet/32/sun--v1.png"
          alt="солнце"/>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ThemeSwiper",
  created() {
    const savedTheme = localStorage.getItem('theme');
    if (savedTheme) {
      this.isDarkMode = savedTheme === 'dark';
    }
  },
  data() {
    return {
      isDarkMode: false
    };
  },
  methods: {
    toggleTheme() {
      this.isDarkMode = !this.isDarkMode;
      localStorage.setItem('theme', this.isDarkMode ? 'dark' : 'light');
    }
  }
};
</script>

<style lang="less" scoped>
 @import 'styles/styles.less';
</style>