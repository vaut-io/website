<script>
	export let start = true;
	export let end = true;
</script>

<div class:start class:end>
	<slot />
</div>

<style>
	div {
		--gutter: var(--space-l-xl);

		margin-inline: auto;
		inline-size: 100%; /* Needed in order to be a flexbox child */
		max-inline-size: calc(var(--fluid-max-width) * 1px);
	}

	.start {
		padding-inline-start: var(--gutter);
	}

	.end {
		padding-inline-end: var(--gutter);
	}
</style>
