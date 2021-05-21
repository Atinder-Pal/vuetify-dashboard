<template>
	<v-container>
		<v-row>
			<v-col>
				<h1>Signup</h1>
				<v-form ref="signUpForm">
					<v-text-field
						label="Email"
						type="email"
						v-model="email"
						:rules="emailRules"
						required
					></v-text-field>
					<v-autocomplete
						label="Which browser do you use?"
						:items="browsers"
					></v-autocomplete>
					<v-file-input
						truncate-length="15"
						label="Attach Profile photo"
						accept="image/*"
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
					<v-checkbox
						label="Agree to terms & conditions"
						v-model="agreeToTerms"
						:rules="agreeToTermsRules"
						required
					></v-checkbox>
					<v-btn type="submit" color="primary" class="mr-4">Submit</v-btn>
					<v-btn color="warning" @click="resetValidation" class="mr-4"
						>Reset validation</v-btn
					>
					<v-btn color="error" @click="resetForm" class="mr-4"
						>Reset Form</v-btn
					>
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
				agreeToTerms: false,

				agreeToTermsRules: [
					(value) =>
						!!value ||
						'You must agree to terms and conditions to create an account',
				],
				email: '',
				emailRules: [
					(value) => !!value || 'Email address is required.',
					(value) => value.indexOf('@') !== 0 || 'Email should have a username',
					(value) => value.includes('@') || 'Email should contain an @ symbol',
				],
			};
		},
		methods: {
			resetValidation() {
				this.$refs.signUpForm.resetValidation();
			},
			resetForm() {
				this.$refs.signUpForm.reset();
			},
		},
	};
</script>
