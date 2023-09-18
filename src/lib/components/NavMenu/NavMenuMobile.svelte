<script lang="ts">
	import { quartInOut } from 'svelte/easing';
	import { fade, fly, slide } from 'svelte/transition';

	export let navItems: {
		name: string;
		href: string;
	}[];
	export let open: boolean = false;
</script>

<nav
	class="fixed w-full h-screen left-0 top-0 z-10 bg-black"
	in:slide={{ duration: 300, easing: quartInOut, axis: 'y' }}
	out:fade={{ duration: 300, easing: quartInOut }}
>
	<div class="containerSizing mt-40 flex flex-col font-light space-y-6 text-2xl uppercase">
		{#each [{ name: 'Home', href: '/' }, ...navItems] as item, i}
			<a
				href={item.href}
				on:click={() => (open = false)}
				class="font-light"
				in:fly|global={{ duration: 500, delay: (i + 1) * 75, easing: quartInOut, x: -50, opacity: 0.1 }}
				>{item.name}
			</a>
		{/each}
	</div>
</nav>
