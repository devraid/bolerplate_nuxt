<script lang="ts">
import { useI18n } from 'vue-i18n'

export default {
	name: 'SignInRegister',
	emits: ['close'],
	setup() {
		const { t } = useI18n()
		return { t }
	},
	data: function() {
		return {
			restPassword: 0,
		}
	},
	methods: {
		register () {
			//npm i -D @vueuse/nuxt @vueuse/core --save
			$fetch(`/api/search/`, {
				method: 'GET',
				params: {
					page: 'test'
				}
			}).then( function( data ){
				console.log(data)
			});
		}
	}
}
</script>

<template>
	<div class="signin-register">
		<UIModalWrapper @close="$emit('close')">
			<div
				v-if="restPassword === 1"
				class="signin flex-1">
				<h4 class="font-avenir-next-heavy text-xl text-gray mb-3">
					{{ t('forgot_password') }}
				</h4>
				<p class="font-avenir-next-book text-base text-gray w-full mb-3">
					{{ t('enter_the_email_address') }}
				</p>
				<input
					class="font-avenir-next-book text-base text-gray w-full px-3 py-2 mb-3 appearance-none outline-none border-solid border border-gray-5 transition-colors focus:border-green-5"
					type="email"
					name="email"
					maxlength="100"
					:placeholder="t('email')"
					autocomplete="email">
				<a
					href="#"
					class="font-avenir-next-book text-sm text-gray underline"
					@click="() => {
						restPassword = 0
					}">{{ t('back_to_sign_in') }}.</a>
				<div class="w-full mt-3">
					<a
						role="button"
						class="inline-block bg-green-7 hover:bg-green-5 font-avenir-next-heavy text-base text-white text-base uppercase px-10 pt-3 pb-2 transition-colors rounded-md"
						@click="() => {
							restPassword = 2
						}">
						{{ t('get_verificcation_code') }}
					</a>
				</div>
			</div>
			<div
				v-if="restPassword === 2"
				class="signin flex-1">
				<h4 class="font-avenir-next-heavy text-xl text-gray mb-3">
					{{ t('forgot_password') }}
				</h4>
				<p class="font-avenir-next-book text-base text-gray w-full mb-3">
					Check your Email and enter the Verification Code and a New Password.
				</p>
				<input
					class="font-avenir-next-book text-base text-gray w-full px-3 py-2 mb-3 appearance-none outline-none border-solid border border-gray-5 transition-colors focus:border-green-5"
					type="text"
					name="verification_code"
					maxlength="50"
					:placeholder="t('verification_code')"
					autocomplete="off">
				<input
					class="font-avenir-next-book text-base text-gray w-full px-3 py-2 mb-3 appearance-none outline-none border-solid border border-gray-5 transition-colors focus:border-green-5"
					type="password"
					name="password"
					maxlength="50"
					:placeholder="t('password')"
					autocomplete="password">
				<input
					class="font-avenir-next-book text-base text-gray w-full px-3 py-2 mb-3 appearance-none outline-none border-solid border border-gray-5 transition-colors focus:border-green-5"
					type="password"
					name="re_new_password"
					maxlength="50"
					:placeholder="t('repeat_password')"
					autocomplete="off">
				<a
					href="#"
					class="font-avenir-next-book text-sm text-gray underline"
					@click="() => {
						restPassword = 0
					}">{{ t('back_to_sign_in') }}.</a>
				<div class="w-full mt-3">
					<a
						role="button"
						class="inline-block bg-green-7 hover:bg-green-5 font-avenir-next-heavy text-base text-white text-base uppercase px-10 pt-3 pb-2 transition-colors rounded-md"
						@click="$emit('close')">
						{{ t('set_new_password') }}
					</a>
				</div>
			</div>
			<div
				v-if="restPassword === 0"
				class="signin flex-1 pb-5 md:pb-0 md:pr-5 max-md:border-b md:border-r border-solid border-gray-3">
				<h4 class="font-avenir-next-heavy text-xl text-gray mb-3">
					{{ t('sign_in') }}
				</h4>
				<input
					class="font-avenir-next-book text-base text-gray w-full px-3 py-2 mb-3 appearance-none outline-none border-solid border border-gray-5 transition-colors focus:border-green-5"
					type="email"
					name="email"
					maxlength="100"
					:placeholder="t('email')"
					autocomplete="email">
				<input
					class="font-avenir-next-book text-base text-gray w-full px-3 py-2 mb-3 appearance-none outline-none border-solid border border-gray-5 transition-colors focus:border-green-5"
					type="text"
					name="password"
					maxlength="50"
					:placeholder="t('password')"
					autocomplete="password">
				<a
					href="#"
					class="font-avenir-next-book text-sm text-gray underline"
					@click="() => {
						restPassword = 1
					}">{{ t('forgot_password') }} {{ t('click_here') }}.</a>
				<div class="w-full mt-3">
					<a
						role="button"
						class="inline-block bg-green-7 hover:bg-green-5 font-avenir-next-heavy text-base text-white text-base uppercase px-10 pt-3 pb-2 transition-colors rounded-md"
						@click="$emit('close')">
						{{ t('sign_in') }}
					</a>
				</div>
			</div>
			<div
				v-if="restPassword === 0"
				class="register flex-1 pt-5 md:pt-0 md:pl-5">
				<h4 class="font-avenir-next-heavy text-xl mb-3">
					{{ t('register') }}
				</h4>
				<input
					class="font-avenir-next-book text-base text-gray w-full px-3 py-2 mb-3 appearance-none outline-none border-solid border border-gray-5 transition-colors focus:border-green-5"
					type="text"
					name="first_name"
					maxlength="100"
					:placeholder="t('first_name')"
					autocomplete="first_name">
				<input
					class="font-avenir-next-book text-base text-gray w-full px-3 py-2 mb-3 appearance-none outline-none border-solid border border-gray-5 transition-colors focus:border-green-5"
					type="text"
					name="last_name"
					maxlength="100"
					:placeholder="t('last_name')"
					autocomplete="last_name">
				<input
					class="font-avenir-next-book text-base text-gray w-full px-3 py-2 mb-3 appearance-none outline-none border-solid border border-gray-5 transition-colors focus:border-green-5"
					type="text"
					name="email"
					maxlength="100"
					:placeholder="t('email')"
					autocomplete="email">
				<input
					class="font-avenir-next-book text-base text-gray w-full px-3 py-2 mb-3 appearance-none outline-none border-solid border border-gray-5 transition-colors focus:border-green-5"
					type="password"
					name="new_password"
					maxlength="50"
					:placeholder="t('password')"
					autocomplete="off">
				<input
					class="font-avenir-next-book text-base text-gray w-full px-3 py-2 mb-3 appearance-none outline-none border-solid border border-gray-5 transition-colors focus:border-green-5"
					type="password"
					name="re_new_password"
					maxlength="50"
					:placeholder="t('repeat_password')"
					autocomplete="off">
				<div class="flex items-center mb-3">
					<input
						id="terms_conditions"
						aria-describedby="checkbox-1"
						type="checkbox"
						class="appearance-none w-5 h-5 cursor-pointer outline-none border-solid border border-gray-5 bg-center bg-no-repeat bg-contain bg-transparent checked:bg-[url('/assets/icons/checkbox.svg')] checked:bg-green-5 checked:border-green-5 h-4 w-4">
					<label
						for="terms_conditions"
						class="font-avenir-next-book text-sm text-gray ml-3">I agree to the <a
							href="#"
							class="font-avenir-next-book text-sm text-gray underline">terms and conditions</a>
					</label>
				</div>
				<a
					role="button"
					class="inline-block bg-green-7 hover:bg-green-5 font-avenir-next-heavy text-base text-white text-base uppercase px-10 pt-3 pb-2 transition-colors rounded-md"
					@click="register()">
					{{ t('free_registration') }}
				</a>
			</div>
		</UIModalWrapper>
	</div>
</template>
