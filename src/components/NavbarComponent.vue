<template>
	<div
		id="tint"
		:class="{ hide: hidden }"
		@click="hideMenu()"
	/>
	<div
		id="burger"
		key="burger"
		:class="{ close: !hidden }"
		@click="hideMenu()"
	>
		<img
			v-if="hidden"
			src="../assets/bmenu.svg"
		/>
		<img
			v-else
			src="../assets/close.svg"
		/>
	</div>
	<nav :class="{ hide: hidden }">
		<div id="name">
			<div id="box">
				Bartłomiej Kowalczyk
				<p>aka. Jarsey45</p>
			</div>
		</div>
		<div
			class="sub"
			:class="{ active: active[0] }"
			@click="subClick(0, 'Projects')"
		>
			My Projects
		</div>
		<div
			class="sub"
			:class="{ active: active[1] }"
			@click="subClick(1, 'About')"
		>
			About Me
		</div>
		<div
			class="sub"
			:class="{ active: active[2] }"
			@click="subClick(2, 'Contact')"
		>
			Contact Me
		</div>
	</nav>
</template>

<script setup>
import { ref } from 'vue'

const emit = defineEmits(['changeComponent'])

const active = ref([true, false, false])
const hidden = ref(true)

function subClick(id, name) {
	const newActive = [false, false, false]
	newActive[id] = true
	active.value = newActive
	emit('changeComponent', name)
}

function hideMenu() {
	hidden.value = !hidden.value
}
</script>

<style lang="scss">
@use '../App' as *;

#tint {
	@media screen and (min-width: 800px) {
		opacity: 0;
		display: none;
	}

	width: 100vw;
	height: 100vh;
	position: fixed;
	background: black;
	z-index: 3;
	top: 0;
	left: 0;
	transition: all 0.5s ease;
	opacity: 0.3;

	&.hide {
		opacity: 0;
		z-index: -1;
	}
}

#burger {
	@media screen and (min-width: 800px) {
		display: none;
	}

	position: fixed;
	z-index: 5;

	left: 0.5em;
	top: 1.2em;

	border-radius: 20%;
	background: $border-color;
	cursor: pointer;
	transition: all 0.5s ease;

	&:hover {
		background: $primary-color;
	}

	img {
		padding: 0.5em 0.5em 0.25em 0.5em;
		height: 1.5em;
		width: 1.5em;
	}

	&.close {
		top: 90%;
		background: $border-color;
	}
}

nav {
	@media screen and (max-width: 800px) {
		position: fixed;
		left: 0;
		transition: left 0.6s ease;
		z-index: 4;
		background: $background-color;
		height: 100%;
	}

	flex: 2;
	border-right: 1px solid $border-color;

	@media screen and (min-width: 801px) {
		font-size: 0.9em;
	}

	@media screen and (min-width: 1030px) {
		@include fontResize();
	}

	&.hide {
		left: -105%;

		@media screen and (max-width: 300px) {
			left: -150%;
			max-width: 100vw;
		}
	}

	#name {
		color: $primary-color;
		cursor: context-menu;
		font-weight: 600;
		font-size: 1.5em;
		padding: 1em;
		border-bottom: 1px solid $border-color;

		p {
			color: hsl(1, 0%, 80%);
			font-size: 0.5em;
		}
	}

	.sub {
		cursor: pointer;

		text-align: left;
		font-size: 1.2em;
		padding: 1em;
		padding-left: 2em;
		height: 1em;
		display: block;
		//overflow: hidden;

		background: linear-gradient(
			to right,
			$primary-color 50%,
			$background-color 50%
		);
		background-size: 200% 101%;
		background-position: right top;
		transition: all 0.5s ease-out;
		border: none;

		&:hover {
			background-position: left bottom;
			padding-left: 3em;
			color: $dark-font-color;
		}

		&.active {
			background: $dark-color;
			padding-left: 3em;
			color: $dark-font-color;
			transition: none;
		}
	}
}
</style>
