<template>
	<main class="columns is-gapledd is multiline">
		<div class="column is-one-quarter">
			<side-bar/>
		</div>
		<div class="column is-three-quarter">

		</div>
	</main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

import sideBar from '@/components/use-cases/side-bar.vue';

export default defineComponent({
	name: 'App',
	components: {
		sideBar,
	}
	});
</script>

<style scoped> 

</style>
