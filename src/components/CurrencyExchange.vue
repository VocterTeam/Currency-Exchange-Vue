<template>
	<div class="currency-exchange">
		<div class="container">
			<form action="#" @submit.prevent="submit">
				<!-- form-group -->
				<div class="form-group">
    			<label for="fsyms">Currency 1</label>
    				<input type="text" class="form-control" id="fsyms" name="fsyms" placeholder="Enter first currency" v-model="formInfo.fsyms">
				</div>
				<!-- END:form-group -->

				<!-- form-group -->
				<div class="form-group">
    			<label for="tsyms">Currency 2</label>
    				<input type="text" class="form-control" id="tsyms" name="tsyms" placeholder="Enter secnd currency" v-model="formInfo.tsyms">
				</div>
				<!-- END:form-group -->
				<button type="submit" class="form-submit btn btn-primary">Check Excnahge of the values</button>
			</form>
			<!-- formOutput -->
			<div id="formOutput">
				<div class="alert form-output"></div>
			</div>
			<!-- END:formOutput -->
		</div>
	</div>
</template>

<script>
export default {
  data () {
    return {
      formInfo: {
        fsym: '',
        tsyms: ''
      },
      formResponse: '',
      apiUrl: 'https://min-api.cryptocompare.com/data/price?'
    }
  },
  methods: {
    submit () {
      this.$http.get(this.apiUrl, {params: this.formInfo})
      .then(response => console.log(response))
    }
  }
}
</script>