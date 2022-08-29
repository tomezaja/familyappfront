<template>
  <div class="app">
      <sidebar />
      <router-view/>
  </div>
</template>

<script setup>
import sidebar from './components/sidebar.vue'
</script>


<style lang="scss">
:root {
	--fresh: #4ABDAC;
	--vermillion: #FC4A1A;
	--sunshine: #F7B733;
	--dark: #334155;
	--light: #DFDCE3;
	--sidebar-width: 250px;
}
* {
	margin: 0;
	padding: 0;
	box-sizing: border-box;
	font-family: 'Fira sans', sans-serif;
}
body {
	background: var(--sunshine);
}
button {
	cursor: pointer;
	appearance: none;
	border: none;
	outline: none;
	background: none;
}
.app {
	display: flex;
	main {
		flex: 1 1 0;
		padding: 2rem;
		@media (max-width: 1024px) {
			padding-left: 6rem;
		}
	}
}

</style>