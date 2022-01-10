<script lang="ts">
	const host = (import.meta.env.VITE_HOST ?? 'http://127.0.0.1:3000').toString();
</script>

<svelte:head>
	<meta name="robots" content="noindex" />
	<meta http-equiv="refresh" content="0; url={host}" />
	<link rel="canonical" href={host} />
</svelte:head>
