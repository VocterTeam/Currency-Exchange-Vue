<template>
	<div class="currency-exchange">
		<div class="container">
			<form action="#" class="form" @submit.prevent="submit">
				<!-- form-group -->
				<div class="form-group">
    			<label for="fsym">Currency 1</label>
    				<input type="text" class="form-control" id="fsym" name="fsym" placeholder="Enter first currency" v-model="formInfo.fsym">
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
			<div id="formOutput" v-if="formResponse.message">
				<div class="form-output alert" :class="{'alert-success': formResponse.success = true, 'alert-danger': formResponse.success === false}">{{formResponseComputed}}</div>
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
      isResponse: false,
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
    submit () {
      this.$http.get(this.apiUrl, {params: this.formInfo})
      .then(response => {
        this.isResponse = true
        this.formResponse.success = true
        this.formResponse.message = `Exchange Rate between ${this.formInfo.fsym} and ${this.formInfo.tsyms} is ${response.bodyText}`
        console.log(response)
      }).catch(error => {
        this.formResponse.success = false
        console.log(error)
      })
    }
  }
}
</script>