<template>
	<div id="app">
    <section class="jumbotron text-center">
      <div class="container">
        <h1 class="jumbotron-heading">Quote Analyzer</h1>
        <p class="lead text-muted">
          A component for comparing and analyzing price quotes of various companies.
        </p>
      </div>
    </section>
		<TableView/>
	</div>
</template>

<script>
	import TableView from './components/TableView.vue'

export default {
  name: 'App',
  components: {
    TableView
  }
}
</script>

<style>
	#app {
		font-family: Avenir, Helvetica, Arial, sans-serif;
		-webkit-font-smoothing: antialiased;
		-moz-osx-font-smoothing: grayscale;
		text-align: center;
		color: #2c3e50;
		margin-top: 60px;
	}
</style>