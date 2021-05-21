<template>
	<v-card>
		<v-card-title>{{ statistic.title }}</v-card-title>
		<v-card-text class="display-2">{{ statistic.value }}</v-card-text>
	</v-card>
</template>

<script lang="ts">
	import { defineComponent } from '@vue/composition-api';
	// export default {
	// 	name: 'StatisticCard',
	// 	props: {
	// 		statistic: {
	// 			type: Object,
	// 			required: true,
	// 		},
	// 	},
	// };

	export default defineComponent({
		name: 'StatisticCard',
		props: {
			statistic: {
				type: Object,
				required: true,
			},
		},
	});
</script>

<style></style>
