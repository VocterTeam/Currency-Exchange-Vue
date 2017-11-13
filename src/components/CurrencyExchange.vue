<template>
	<div class="currency-exchange">
		<div class="container">
			<form action="#" @submit.prevent="submit">
				<!-- form-group -->
				<div class="form-group">
    			<label for="exampleInputEmail1">XXX</label>
    				<input type="text" class="form-control" id="xxx" name="xxx" placeholder="Enter first currency">
				</div>
				<!-- END:form-group -->

				<!-- form-group -->
				<div class="form-group">
    			<label for="exampleInputEmail1">YYY</label>
    				<input type="text" class="form-control" id="yyy" name="yyy" placeholder="Enter secnd currency">
				</div>
				<!-- END:form-group -->
				<button type="submit" class="form-submit btn btn-primary">Check Excnahge of the values</button>
			</form>
		</div>
	</div>
</template>

<script>
export default {
  data () {
    return {
      apiUrl: 'https://www.cryptocompare.com/api/#-'
    }
  },
  methods: {
    submit () {
      this.$http.get(this.apiUrl + '10')
      .then(response => console.log(response))
    }
  }
}
</script>