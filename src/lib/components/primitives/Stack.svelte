<script lang="ts">
	// In some cases, browsers should interpret the Stack as a list for screen reader software
	export let list = false;
	// Whether the spaces apply recursively (i.e. regardless of nesting level)
	export let deep = false;
	// A CSS margin value
	export let space = 0;
	// The element after which to split the stack with an auto margin
	export let splitAfter: number = 0;
</script>

<svelte:element
	this={list ? 'ul' : 'div'}
	role={list ? 'list' : undefined}
	class:shallow={!deep}
	class:deep
	class:split={splitAfter}
	style="--space: var(--s{space}); --split-after: {splitAfter}"
>
	<slot />
</svelte:element>

<style>
	.shallow,
	.deep {
		/* The flex context */
		display: flex;
		flex-direction: column;
		justify-content: flex-start;
	}
	.shallow > :global(*) {
		/* Any extant vertical margins are removed */
		margin-block: 0;
	}
	.shallow > :global(*) + :global(*) {
		/* Top margin is only applied to successive elements */
		margin-block-start: var(--space);
	}
	.deep :global(*) {
		margin-block: 0;
	}
	.deep :global(*) + :global(*) {
		margin-block-start: var(--space);
	}

	/*
	.shallow.split > :global(:nth-child(0)) {
		margin-block-end: auto;
	}
	.deep.split :global(:nth-child(0)) {
		margin-block-end: auto;
	}
	*/
</style>
