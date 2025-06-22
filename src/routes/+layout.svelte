<script lang="ts">
	import '../app.css';

	import { Navigation } from '@skeletonlabs/skeleton-svelte';
	import IconMenu from '@lucide/svelte/icons/menu';
	import IconSun from '@lucide/svelte/icons/sun';
	import IconWind from '@lucide/svelte/icons/wind';
	import IconSettings from '@lucide/svelte/icons/settings';

	let isExpansed = $state(false);

	function toggleExpanded() {
		isExpansed = !isExpansed;
	}

	let { children } = $props();
</script>

<div class="card border-surface-100-900 grid h-[760px] w-full grid-cols-[auto_1fr] border-[1px]">
	<Navigation.Rail expanded={isExpansed}>
		{#snippet header()}
			<Navigation.Tile labelExpanded="Menu" onclick={toggleExpanded} title="Toggle Menu Width"
				><IconMenu /></Navigation.Tile
			>
		{/snippet}

		{#snippet tiles()}
			<Navigation.Tile labelExpanded="Solar panels" href="/solar" title="Solar panels">
				<IconSun />
			</Navigation.Tile>
			<Navigation.Tile labelExpanded="Wind turbine" href="/wind" title="Wind turbine">
				<IconWind />
			</Navigation.Tile>
		{/snippet}

		{#snippet footer()}
			<Navigation.Tile labelExpanded="Settings" href="/settings" title="Settings">
				<IconSettings />
			</Navigation.Tile>
		{/snippet}
	</Navigation.Rail>
	<div class="flex items-center justify-center">
		{@render children()}
	</div>
</div>
