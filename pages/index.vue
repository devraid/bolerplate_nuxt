<script lang="ts">
import { useI18n } from 'vue-i18n'

export default {
	name: 'IndexPage',
	components: {},
	setup() {
		const { t } = useI18n()
		return { t}
	},
	data: function() {
		return {
			visibleSignRegister: true
		}
	},
	mounted () {
		this.$nextTick(function () {
			let everythingLoaded = setInterval(function (scope) {
				if (/loaded|complete/.test(document.readyState)) {
					clearInterval(everythingLoaded)
					console.log('Fonts and images are loaded, let\'s start the show!')
					scope.init()
				}
			}, 10, this)
		})
	},
	methods: {
		init () {
			console.log('Fully loaded.')
		}
	}
}
</script>

<template>
	<main class="home flex flex-col px-5 bg-white md:bg-gray-2">
		<Header />
		<div class="container flex flex-1 min-h-full mx-auto px-5 bg-white">
			<FormsSignInRegister
				v-if="visibleSignRegister"
				@close="() => {
					visibleSignRegister = false
				}" />
		</div>
	</main>
</template>
