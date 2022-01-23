<template>
	<header>
		<div class="text-center sm:text-white text-gray-800 p-4 mb-4 bg-yellow-800 sm:bg-gray-900">
			<h1 class="text-3xl md:text-5xl uppercase font-semibold my-10">
				<i class="fa fa-viruses text-3xl text-yellow-400"></i>
				 Covid-19 Update ({{ text }})
			</h1>
		</div>
	</header>
</template>

<script>
export default {
  name: 'Header',
  props: ['text'],
  methods: {

  }
}
</script>