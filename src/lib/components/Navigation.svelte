<script lang="ts">
	// components
	import BaseImage from '$lib/util/BaseImage.svelte';

	// stores
	import { phone, fullAddress, email, socials, pages } from '$lib/config';
	import { page } from '$app/stores';

	// styles
	import '$styles/layout/navigation.less';

	// logic
	let isActive = false;

	const toggle = () => {
		isActive = !isActive;
		document.body.classList.toggle('is-active');
	};

	let y: any;
</script>

<svelte:window bind:scrollY={y} />

<header class={y >= 100 ? 'scroll' : ''}>
	<nav>
		<div class="inner-nav" class:isActive>
			<!-- mobile logo or 'Menu' text -->

			<ul class="links">
				<!-- pages - controlled by config -->
				{#each pages as { pageName, path }}
					<li class:active={$page.url.pathname === path} class="link">
						<a href={path} on:click={toggle}>{pageName}</a>
					</li>
				{/each}
			</ul>
		</div>
	</nav>

	<button class="hamburger" class:isActive aria-label="toggle" on:click={toggle}>
		<span class="box">
			<span class="inner" />
			<span class="inner" />
			<span class="inner" />
		</span>
	</button>
</header>
