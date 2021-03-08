<template>
	<section class="section">
		<div class="container">
			<h1 class="title">
				Comentários
			</h1>
      <Comments />
    </div>
  </section>
</template>

<script>
import './assets/bulma.min.css'
import Comments from './components/Comments'
export default {
  name: 'App',
  components: {
    Comments,
  }
}
</script>

<style>
</style>