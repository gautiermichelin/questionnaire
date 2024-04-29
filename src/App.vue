<script>
export default {
  methods: {
    submitForm(data) {
		console.log('Form submitted');
		//console.log(this.$route.query.test) // outputs 'yay'
		let urlParams = new URLSearchParams(window.location.search);
    	console.log(urlParams.has('test')); // true
    	console.log(urlParams.get('test')); // "MyParam"
      	//this.$formkit.submit('questionnaire')
		console.log(data);
		//console.log(this.$formkit);
    }
  },
}
</script>

<template>
	<FormKit type="form" #default="{ value }" 
    :actions="false"
	id="questionnaire"
	action="https://formtester.goodbytes.be/post.php"
	method="post"
    @submit="submitForm"
	form-class="outer-container" :config="{
		validationVisibility: 'dirty',
	}">
		<h1>Questionnaire début de formation</h1>
		<h3>Merci de répondre aux questions suivantes :</h3>
		<div class="input-group">
			<FormKit type="text" label="Prénom" placeholder="Prénom" validation="required|length:3"></FormKit>

			<FormKit type="text" label="Nom de famille" placeholder="Nom" validation="required|length:3"></FormKit>
		</div>
<!--
			<FormKit type="date" label="Date of Birth" validation="required|date_before:2023-01-01"></FormKit>

		<div class="input-group">
			<FormKit type="text" label="Gender" placeholder="Your gender" validation="required"></FormKit>

			<FormKit type="text" label="Phone number" suffix-icon="telephone" placeholder="555-5555-555"
				validation="required"></FormKit>

		</div>
		<FormKit type="text" label="Address" placeholder="21st Random Street" validation="required"></FormKit>

		<FormKit type="email" label="Email address" placeholder="JohnDoe@gmail.com" suffix-icon="email"
			validation="required|email"></FormKit>

			<FormKit
  type="radio"
  label="Do you have a doctor you would prefer to attend to you?"
  name="preferred"
  :options="['Yes', 'No']"
  validation="required"
></FormKit>

<FormKit
  v-if="value.preferred === 'Yes'"
  type="text"
  label="What's the name of this doctor?"
  validation="required"
></FormKit>
<FormKit
  type="select"
  label="Which procedure do you want done?"
  :options="['Check up', 'Result analysis', 'Medical exam']"
  placeholder="Select a procedure"
  validation="required"
></FormKit>

<FormKit
  type="datetime-local"
  label="Preferred appointment date and time"
  validation="required"
></FormKit>
-->
		<FormKit type="submit" label="Valider"></FormKit>
	</FormKit>
</template>

<style>
.outer-container {
	width: 400px;
	border: 1px solid #e4e4e4;
	padding: 1.5em;
	border-radius: 1em;
	margin: 0 auto 1em auto;
}

.input-group {
	display: flex;
	gap: 1em;
}

h1,
h3 {
	text-align: center;
}
</style>