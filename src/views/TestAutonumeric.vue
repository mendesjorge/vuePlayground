<template>
	<div class="">
		<p>
			moment in action
		</p> 
		{{date | moment('DD MMM YYYY')}}
	</div>
</template>
<script>
	export default{
		data(){
			return {
				date: new Date()
			}
		},
		beforeCreate(){
			this.$moment.locale('pt', {
				monthsShort:['JAN', 'FEV','MAR','ABR','MAI','JUN','JUL','AGO','SET','OUT','NOV','DEZ']
			})
		}
	}
</script>
<styles>
	
</styles>