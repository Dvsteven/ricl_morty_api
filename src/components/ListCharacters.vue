<template>
	<section>
	  <div class="characters">
		<div class="characters__item" v-for="character in characters" :key="character.id">
		  <CardCharacter :character="character" />
		</div>
	  </div>
	</section>
  </template>


<script>
import { computed, onMounted } from 'vue'
import { useStore } from 'vuex'

import CardCharacter from '@/components/CardCharacter'

export default {
	components: {
		CardCharacter
	},
	SetUp(){
		const store = useStore()
		const characters = computed(() => {
			return store.state.charactersFilter
		})
		onUnmounted(() => {
			store.dispatch('getCharacters')
		})

		return{
			characters
		}
	}
}
</script>

<style>

</style>