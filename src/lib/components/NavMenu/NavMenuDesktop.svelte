<script lang="ts">
	export let navItems: {
		name: string;
		href: string;
	}[];
</script>

<section class="md:flex items-center space-x-6 hidden md:space-x-8">
	{#each navItems as item}
		<a href={item.href} class="">{item.name}</a>
	{/each}
</section>
