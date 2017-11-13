<template>
	<div class="currency-exchange">
		<div class="container">
			<form action="#" class="form" @submit.prevent="submit">
				<!-- form-group -->
				<div class="form-group">
    			<label for="fsym">Currency 1</label>
    				<input type="text" class="form-control" id="fsym" name="fsym" placeholder="Enter first currency" v-model.trim="formInfo.fsym">
				</div>
				<!-- END:form-group -->

				<!-- form-group -->
				<div class="form-group">
    			<label for="tsyms">Currency 2</label>
    				<input type="text" class="form-control" id="tsyms" name="tsyms" placeholder="Enter secnd currency" v-model.trim="formInfo.tsyms">
				</div>
				<!-- END:form-group -->
				<button type="submit" class="form-submit btn btn-primary">Show exchange Rate</button>
			</form>
			<!-- formOutput -->
			<div id="formOutput" v-if="formResponse.message">
				<div class="form-output alert" :class="[formResponse.success ? 'alert-success' : 'alert-danger']">{{formResponseComputed}}</div>
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
      formResponse: {
        message: '',
        success: false
      },
      apiUrl: 'https://min-api.cryptocompare.com/data/price?'
    }
  },
  computed: {
    formResponseComputed () {
      return this.formResponse.message
    }
  },
  methods: {
    formDataToUpperCase () {
      this.formInfo.fsym = this.formInfo.fsym.toUpperCase()
      this.formInfo.tsyms = this.formInfo.tsyms.toUpperCase()
    },
    submit () {
      this.formDataToUpperCase()
      this.$http.get(this.apiUrl, {params: this.formInfo})
      .then(response => {
        if (this.formInfo.fsym !== '' && this.formInfo.tsyms !== '') {
          this.formResponse.success = true
          this.formResponse.message = `Exchange Rate between ${this.formInfo.fsym} and ${this.formInfo.tsyms} is ${response.body[this.formInfo.tsyms]}`
        } else {
          this.formResponse.success = false
          this.formResponse.message = 'Please, fill all fields'
        }
        console.log(response.body)
      }).catch(error => {
        this.formResponse.success = false
        console.log('error', error)
      })
    }
  }
}
</script>