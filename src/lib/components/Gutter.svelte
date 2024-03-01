<script>
    export let start = true;
    export let end = true;
</script>

<div class:start class:end>
    <slot />
</div>

<style>
    div {
        margin-inline: auto;
        inline-size: 100%; /* Needed in order to be a flexbox child */
        max-inline-size: calc(var(--f-max-w) * 1px);
    }

    .start {
        padding-inline-start: var(--s1);
    }

    .end {
        padding-inline-end: var(--s1);
    }
</style>

