<template>
	<div id="flexbox">
		<NavbarComponent @change-component="changeComp" />
		<ProjectsPage v-if="chosenComp === Component.Projects" />
		<AboutPage v-if="chosenComp === Component.About" />
		<ContactPage v-if="chosenComp === Component.Contact" />
	</div>
</template>

<script setup>
import { ref } from 'vue'
import NavbarComponent from './components/NavbarComponent.vue'
import ProjectsPage from './components/ProjectsPage.vue'
import AboutPage from './components/AboutPage.vue'
import ContactPage from './components/ContactPage.vue'

const Component = Object.freeze({
	Projects: 'Projects',
	About: 'About',
	Contact: 'Contact',
})

const chosenComp = ref(Component.Projects)

function changeComp(name) {
	chosenComp.value = name
}
</script>

<style lang="scss">
@use './App' as *;

#app {
	width: 100%;
	height: 100%;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: $default-font-color;
}

#flexbox {
	width: 100%;
	height: 100%;
	display: flex;
}
</style>
