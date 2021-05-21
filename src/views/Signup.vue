<template>
	<v-container>
		<v-row>
			<v-col>
				<h1>Signup</h1>
				<v-form>
					<v-text-field label="Email" type="email"></v-text-field>
					<v-autocomplete
						label="Which browser do you use?"
						:items="browsers"
					></v-autocomplete>
					<v-file-input
						truncate-length="15"
						label="Attach Profile photo"
					></v-file-input>
					<v-dialog
						ref="dialog"
						v-model="modal"
						:return-value.sync="date"
						persistent
						width="290px"
					>
						<template v-slot:activator="{ on, attrs }">
							<v-text-field
								v-model="date"
								label="Picker in dialog"
								prepend-icon="mdi-calendar"
								readonly
								v-bind="attrs"
								v-on="on"
							></v-text-field>
						</template>
						<v-date-picker v-model="date" scrollable>
							<v-spacer></v-spacer>
							<v-btn text color="primary" @click="modal = false">
								Cancel
							</v-btn>
							<v-btn text color="primary" @click="$refs.dialog.save(date)">
								OK
							</v-btn>
						</v-date-picker>
					</v-dialog>
					<v-checkbox label="Agree to terms & conditions"></v-checkbox>
					<v-btn type="submit" color="primary">Submit</v-btn>
				</v-form>
			</v-col>
		</v-row>
	</v-container>
</template>

<script>
	export default {
		data() {
			return {
				browsers: [
					'Chrome',
					'Safari',
					'Firefox',
					'Edge',
					'Internet Explorer',
					'Brave',
				],
				date: new Date().toISOString().substr(0, 10),

				modal: false,
			};
		},
	};
</script>
