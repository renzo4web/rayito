<script lang="ts">
	import '../app.css';
</script>

<div class="container mx-auto px-10">
	<div class="navbar bg-lime-100 rounded-2xl mt-5">
		<div class="navbar-start">
			<a href="/" class="btn btn-ghost normal-case text-xl">Rayito</a>
		</div>
		<div class="navbar-end">
			<a href="/app" class="btn">APP</a>
		</div>
	</div>

	<div class="py-10">
		<slot />
	</div>
</div>
