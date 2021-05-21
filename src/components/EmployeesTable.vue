<template>
	<v-data-table
		:headers="headers"
		:items="employees"
		:items-per-page="5"
		class="elevation-1"
		@click:row="selectRow"
		:multi-sort="true"
	></v-data-table>
</template>

<script lang="ts">
	import { defineComponent, reactive, toRefs } from '@vue/composition-api';
	// export default {
	// 	name: 'EmployeesTable',
	// 	props: {
	// 		employees: {
	// 			type: Array,
	// 			required: true,
	// 		},
	// 	},
	// 	data: () => ({
	// 		headers: [
	// 			{ text: 'Employee ID', value: 'id' },
	// 			{ text: 'Name', value: 'name' },
	// 			{ text: 'Position Title', value: 'title' },
	// 			{ text: 'Salary', value: 'salary' },
	// 		],
	// 	}),
	// 	methods: {
	// 		selectRow(event) {
	// 			const employee = {
	// 				name: event.name,
	// 				title: event.title,
	// 			};
	// 			this.$emit('select-employee', employee);
	// 		},
	// 	},
	// };

	export default defineComponent({
		name: 'EmployeesTable',
		props: {
			employees: {
				type: Array,
				required: true,
			},
		},
		setup(props, context) {
			const state = reactive({
				headers: [
					{ text: 'Employee ID', value: 'id' },
					{ text: 'Name', value: 'name' },
					{ text: 'Position Title', value: 'title' },
					{ text: 'Salary', value: 'salary' },
				],
			});

			const selectRow = (event) => {
				const employee = {
					name: event.name,
					title: event.title,
				};
				context.emit('select-employee', employee);
			};

			return { ...toRefs(state), selectRow };
		},
	});
</script>

<style></style>
