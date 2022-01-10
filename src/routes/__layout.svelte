<script lang="ts">
	const author = (import.meta.env.VITE_AUTHOR ?? '').toString();
	const name = (import.meta.env.VITE_SITE_NAME ?? '').toString();
	const host = (import.meta.env.VITE_HOST ?? 'http://127.0.0.1:3000').toString();
	const desc = (import.meta.env.VITE_DESCRIPTION ?? '').toString();
	const gsv = (import.meta.env.VITE_GOOGLE_SITE_VERIFICATION ?? '').toString();
	const monetization = (import.meta.env.VITE_MONETIZATION ?? '').toString();

	const url = `${host}${import.meta.env.BASE_URL}`;
</script>

<svelte:head>
	<meta name="author" content={author} />
	<meta name="description" content={desc} />
	<meta name="google-site-verification" content={gsv} />
	<meta name="monetization" content={monetization} />
	<meta property="og:site_name" content={name} />
	<meta property="og:title" content={name} />
	<meta property="og:description" content={desc} />
	<meta property="og:url" content={url} />
	<meta name="twitter:title" content={name} />
	<meta name="twitter:description" content={desc} />
	<title>{name}</title>

	<link rel="preconnect" href="https://fonts.gstatic.com" />
	<link
		rel="stylesheet"
		href="https://fonts.googleapis.com/css2?family=Roboto+Condensed:wght@400;700&family=Roboto:wght@300;400;700&display=swap"
	/>
</svelte:head>

<slot />
