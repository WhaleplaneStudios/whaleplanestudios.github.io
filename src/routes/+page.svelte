<script lang="ts">
	import GameHoverButton from '$lib/components/game-hover-button.svelte';
	import SocialMediaButtonsRow from '$lib/components/social-media-buttons-row.svelte';
	import { Button } from '$lib/components/ui/button/index.js';
</script>

<!-- Logo banner -->
<img alt="WhaleplaneStudios logo banner" src="banner-2024.png" />

<!-- Game info buttons grid -->
<div class="grid grid-rows-2 grid-col-3 grid-flow-col place-content-center mt-6">
	<div class="row-span-2">
		<GameHoverButton
			altText="Gonzalo the Chicken Episode 1"
			hoveredImage="gonzalo-episode-1-hovered.png"
			unhoveredImage="gonzalo-episode-1.png"
		/>
	</div>
	<GameHoverButton
		altText="The Seven Seas"
		hoveredImage="the-seven-seas-hovered.png"
		unhoveredImage="the-seven-seas.png"
	/>
	<GameHoverButton
		altText="Rolliosis"
		hoveredImage="rolliosis-hovered.png"
		unhoveredImage="rolliosis.png"
	/>
	<GameHoverButton
		altText="Procedure"
		hoveredImage="procedure-hovered.png"
		unhoveredImage="procedure.png"
	/>
</div>

<!-- Social media buttons with hover text -->
<SocialMediaButtonsRow />
