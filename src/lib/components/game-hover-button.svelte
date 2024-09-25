<script lang="ts">
	import { Button } from '$lib/components/ui/button/index.js';

	export let hoveredImage;
	export let unhoveredImage;
	export let altText;

	$: hovered = false;
</script>

<Button
	variant="image"
	size="game_tile"
	on:mouseenter={() => (hovered = true)}
	on:mouseleave={() => (hovered = false)}
>
	<img alt={altText} src={hovered ? hoveredImage : unhoveredImage} />
</Button>
