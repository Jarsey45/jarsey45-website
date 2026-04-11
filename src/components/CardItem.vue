<template>
	<div class="card">
		<div class="nav-box">
			<div>
				<div
					class="link"
					@click="toLink"
				>
					Preview!
				</div>
			</div>
			<div class="title">
				{{ title }}
			</div>
			<div>
				<img
					class="github"
					src="../assets/github64.png"
					alt="github"
					@click="toGithub"
				/>
			</div>
		</div>
		<div class="divider" />
		<div class="description">
			{{ desc }}
		</div>
		<div class="lang-box">
			<div class="lang-left">Used technologies</div>
			<div class="lang-right">
				<span
					v-for="(l, index) of lang"
					:key="index"
				>
					{{ l }}</span
				>
			</div>
		</div>
		<div class="date">Uploaded {{ date }}</div>
	</div>
</template>

<script setup>
const props = defineProps({
	title: { type: String, required: true },
	desc: { type: String, required: true },
	lang: { type: Array, required: true },
	link: { type: String, required: true },
	github: { type: String, required: true },
	date: { type: String, required: true },
})

function toGithub() {
	window.location.href = props.github
}

function toLink() {
	window.location.href = props.link
}
</script>

<style></style>
