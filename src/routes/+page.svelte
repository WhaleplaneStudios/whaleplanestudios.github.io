<script lang="ts">
	import GameHoverButton from '$lib/components/game-hover-button.svelte';
	import SocialMediaTooltipButton from '$lib/components/social-media-tooltip-button.svelte';
	import { Button } from '$lib/components/ui/button/index.js';

	$: selectedTab = 'games';
</script>

<!-- Logo banner -->
<img alt="WhaleplaneStudios logo banner" src="banner-2024.png" />

<div class="flex justify-center">
	<div class="grid grid-rows-1 grid-flow-col space-x-16 mt-10 mb-6">
		<div class="justify-self-start space-x-2">
			<!-- Nav Buttons -->
			<Button
				size="icon"
				variant={selectedTab === 'games' ? 'default' : 'outline'}
				class="text-2xl min-w-fit px-3"
				on:click={() => (selectedTab = 'games')}>Our Games</Button
			>
			<Button
				size="icon"
				variant={selectedTab === 'team' ? 'default' : 'outline'}
				class="text-2xl min-w-fit px-3"
				on:click={() => (selectedTab = 'team')}>Our Team</Button
			>
		</div>
		<div class="justify-self-end space-x-2">
			<!-- Social media links -->
			<SocialMediaTooltipButton
				link="https://discord.gg/ggkatrDpmv"
				tooltipText="Chat with us on Discord!"
				icon="ic:baseline-discord"
			/>
			<SocialMediaTooltipButton
				link="https://whaleplanestudios.itch.io/"
				tooltipText="Play our games on itch.io!"
				icon="cib:itch-io"
			/>
			<SocialMediaTooltipButton
				link="https://www.youtube.com/channel/UCSk-EZSzULqEszKrE2j361Q"
				tooltipText="Watch our videos on YouTube!"
				icon="mdi:youtube"
			/>
			<SocialMediaTooltipButton
				link="https://www.facebook.com/WhaleplaneStudios"
				tooltipText="Like us on Facebook!"
				icon="ic:baseline-facebook"
			/>
			<SocialMediaTooltipButton
				link="https://www.instagram.com/whaleplanestudios/"
				tooltipText="Follow us on Instagram!"
				icon="ri:instagram-fill"
			/>
		</div>
	</div>
</div>

{#if selectedTab === 'games'}
	<!-- Games List -->
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
{/if}

{#if selectedTab === 'team'}team stuff go here{/if}
