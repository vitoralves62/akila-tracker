<template>
	<main class="columns is-gapless is multiline">
		<div class="column is-one-quarter">
			<side-bar/>
		</div>
		<div class="column is-three-quarter">
			<principal-form/>
		</div>
	</main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

import sideBar from '@/components/use-cases/side-bar.vue';
import principalForm from './components/use-cases/principal-form.vue';

export default defineComponent({
	name: 'App',
	components: {
		sideBar,
		principalForm,
	}
	});
</script>

<style scoped> 

</style>
