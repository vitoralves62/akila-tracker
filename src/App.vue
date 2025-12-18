<template>
	<main 
		class="columns is-gapless is multiline" 
		:class="{'dark-mode': darkModeActived}"
	>
		<div class="column is-one-quarter">
			<side-bar @change-color-theme="changeColorTheme"/>
		</div>
		<div class="column is-three-quarter content">
			<principal-form @add-task="saveTask"/>
			<div v-if="tasks.length > 0" class="list">
				<ui-task
					v-for="(task, index) in tasks"
					:key="index"
					:task="task"
				/>
			</div>
			<div v-else class="list">
				<box-template>
					Nenhuma tarefa registrada hoje.
				</box-template>
			</div>
		</div>
	</main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

import boxTemplate from '@/templates/box-template.vue';
import sideBar from '@/components/use-cases/side-bar.vue';
import principalForm from '@/components/use-cases/principal-form.vue';
import uiTask from '@/components/ui/ui-task.vue';
import ITask from '@/interfaces/ITask';

export default defineComponent({
	name: 'App',
	components: {
		sideBar,
		principalForm,
		uiTask,
		boxTemplate,
	},
	data (){
		return {
			tasks: [] as ITask[],
			darkModeActived: false
		}
	},

	methods: {
		saveTask(task: ITask){
			this.tasks.push(task);
		},

		changeColorTheme(darkModeActived: boolean){
			this.darkModeActived = darkModeActived;
		}
	}
});
</script>

<style scoped> 
:root {
  color-scheme: light dark; /* Ou 'light dark' se quiseres suportar ambos manualmente */
}

.list{
	padding: 1.5rem;
}

main {
	--bg-primary: #FFF;
	--text-primary: #000;
}

main.dark-mode{
	--bg-primary: #2b2d42;
	--text-primary: #ddd;
}

.content{
	background-color: var(--bg-primary);
}
</style>
