<script lang="ts">
	import { onMount } from 'svelte';

	let urls = [
		{
			name: 'Loading latest article...',
			url: 'https://clavinjune.dev/'
		},
		{
			name: 'Email',
			url: 'mailto:juneardoc@gmail.com'
		},
		{
			name: 'Github',
			url: 'https://github.com/ClavinJune/'
		},
		{
			name: 'LinkedIn',
			url: 'https://linkedin.com/in/juneardoc/'
		},
		{
			name: 'Secreto',
			url: 'https://secreto.site/ancpq5'
		},
		{
			name: 'Twitter',
			url: 'https://twitter.com/clavinjune/'
		}
	];

	onMount(async () => {
		let item = await fetch('https://clavinjune.dev/en/index.xml')
			.then((resp) => resp.text())
			.then((str) => new DOMParser().parseFromString(str, 'text/xml'))
			.then((data) => {
				let item = data.querySelector('item');
				return {
					name: `Latest Article - ${item.querySelector('title').innerHTML}`,
					url: `${
						item.querySelector('link').innerHTML
					}?utm_source=link_clavinjune_dev&utm_medium=organic_social&utm_term=social_media&utm_content=text`
				};
			});

		urls[0] = item;
	});
</script>

<div class="center title">{import.meta.env.VITE_AUTHOR}</div>

<div class="center">
	{#each urls as u}
		<a class="center card" href={u.url} rel="noreferrer noopener" target="_blank">
			{u.name}
		</a>
	{/each}
</div>

<style lang="scss">
	$black: #333;
	$gray: rgba(51, 51, 51, 0.2);
	$red: #ec5f5f;
	$phone-portrait: 'only screen and (max-width: 480px)';

	.center {
		text-align: center;
		width: 100%;
	}

	a {
		color: $black;
		text-decoration: none;
	}

	div.title {
		font-family: roboto condensed, sans-serif;
		font-size: 40px;
		font-weight: 800 !important;
		margin-top: 3rem;
		line-height: 50px;
	}

	a.card {
		border: solid 1px $gray;
		border-radius: 5px;
		display: block;
		margin: 1.5rem 20%;
		line-height: 40px;
		width: 60%;

		@media #{$phone-portrait} {
			font-size: 24px;
			margin: 1.5rem 5%;
			width: 90%;
		}

		&:hover {
			text-decoration: underline;
			text-decoration-color: $red;
			text-decoration-thickness: 15%;
		}
	}
</style>
