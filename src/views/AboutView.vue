<template>
	<div class="container">
		<p>这里是页面</p>
		<button @click="toggleTheme(1)">默认主题</button>
		<button @click="toggleTheme(0)">暗黑主题</button>
	</div>
</template>

<script>
export default {
	data() {
		return {
			theme: 'light',
		};
	},
  created () {
    this.toggleTheme(1)

  },
	methods: {
		toggleTheme(index) {
			window.document.documentElement.setAttribute(
				'data-theme',
				index === 0 ? 'light' : 'dark'
			);
		},
	},
};
</script>

<style lang="scss" scoped>
@import '@/assets/scss/handle.scss';
.container {
  p {
    border: 3px solid ;
    @include font_color('font_color1');
    @include border_color('border_color1');
    @include content_color('content_color1');
  }
}
</style>
