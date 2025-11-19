<script lang="ts">
	import GameHoverButton from '$lib/components/game-hover-button.svelte';
	import SocialMediaTooltipButton from '$lib/components/social-media-tooltip-button.svelte';
	import { Button } from '$lib/components/ui/button/index.js';

	let innerWidth = 0;
	let innerHeight = 0;

	$: selectedTab = 'games';
	$: isScreenPortrait = innerWidth * 1.33 <= innerHeight;
</script>

<!-- Record the current screen size for image switching -->
<svelte:window bind:innerWidth bind:innerHeight />

<!-- Logo banner -->
<div class="w-full items-center">
	<img
		alt="WhaleplaneStudios logo banner"
		src={isScreenPortrait ? 'top-banner-2025-mobile.png' : 'top-banner-2025-wide.png'}
		class="mx-auto"
	/>
</div>

<!-- Buttons row -->
<div class="flex justify-center">
	<div
		class="grid grid-rows-2 lg:grid-rows-1 grid-flow-col space-y-2 lg:space-x-16 lg:space-y-0 mt-10 mb-6"
	>
		<!-- Nav buttons -->
		<div class="justify-self-center lg:justify-self-start space-x-2">
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
		<!-- Social media links -->
		<div class="justify-self-center lg:justify-self-end space-x-2">
			<SocialMediaTooltipButton
				link="https://store.steampowered.com/app/4117840/Gonzalo_the_Chicken__Episode_I/"
				tooltipText="Wishlist on Steam!"
				icon="mdi:steam"
			/>
			<SocialMediaTooltipButton
				link="https://discord.gg/ggkatrDpmv"
				tooltipText="Chat with us on Discord!"
				icon="ic:baseline-discord"
			/>
			<SocialMediaTooltipButton
				link="https://www.youtube.com/channel/UCSk-EZSzULqEszKrE2j361Q"
				tooltipText="Watch our videos on YouTube!"
				icon="mdi:youtube"
			/>
			<SocialMediaTooltipButton
				link="https://www.instagram.com/whaleplanestudios/"
				tooltipText="Follow us on Instagram!"
				icon="ri:instagram-fill"
			/>
			<SocialMediaTooltipButton
				link="https://www.facebook.com/WhaleplaneStudios"
				tooltipText="Like us on Facebook!"
				icon="ic:baseline-facebook"
			/>
		</div>
	</div>
</div>

<!-- Games tab -->
{#if selectedTab === 'games'}
	<!-- Games List -->
	<div class="flex flex-col items-center gap-4 p-4 max-w-5xl mx-auto">
		<div class="w-full text-center">
			<GameHoverButton
				altText="Gonzalo the Chicken Episode 1"
				hoveredImage="gonzalo-episode-1-hovered.png"
				unhoveredImage="gonzalo-episode-1.png"
				link="https://store.steampowered.com/app/4117840/Gonzalo_the_Chicken__Episode_I/"
			/>
		</div>

		<div class="grid grid-cols-1 md:grid-cols-3 gap-4 w-full">
			<GameHoverButton
				altText="The Seven Seas"
				hoveredImage="the-seven-seas-hovered.png"
				unhoveredImage="the-seven-seas.png"
				link="https://whaleplanestudios.itch.io/the-seven-seas"
			/>
			<GameHoverButton
				altText="Rolliosis"
				hoveredImage="rolliosis-hovered.png"
				unhoveredImage="rolliosis.png"
				link="https://whaleplanestudios.itch.io/rolliosis"
			/>
			<GameHoverButton
				altText="Procedure"
				hoveredImage="procedure-hovered.png"
				unhoveredImage="procedure.png"
				link="https://whaleplanestudios.itch.io/procedure"
			/>
		</div>
	</div>
{/if}

<!-- Team tab -->
{#if selectedTab === 'team'}
	<div
		class="grid grid-rows-3 lg:grid-rows-1 grid-col-1 lg:grid-col-2 grid-flow-col place-content-center mt-6 mb-24 space-y-2 lg:space-x-24 lg:space-y-0"
	>
		<div class="flex flex-col items-center text-center">
			<img alt="Jeremy" src="team-jeremy.jpg" class="w-72 rounded-full" />
			<p class="text-2xl">Jeremy Neville</p>
			<p class="text-large mb-2">President</p>
			<i
				><p class="text-xl">Top 3 favorite games:</p>
				<p class="text-large">Jak and Daxter | Half-Life: Alyx | Minecraft</p>
			</i>
		</div>
		<div class="flex flex-col items-center text-center">
			<img alt="Jake" src="team-jake.jpg" class="w-72 rounded-full" />
			<p class="text-2xl">Jake Facius</p>
			<p class="text-large mb-2">Vice President</p>
			<i
				><p class="text-xl">Top 3 favorite games:</p>
				<p class="text-large">Super Mario Sunshine | Return of the Obra Dinn | Portal 2</p>
			</i>
		</div>
		<div class="flex flex-col items-center text-center">
			<img alt="Anders" src="team-anders.jpg" class="w-72 rounded-full" />
			<p class="text-2xl">Anders Beckman</p>
			<p class="text-large mb-2">Music Production</p>
			<i
				><p class="text-xl">Top 3 favorite games:</p>
				<p class="text-large">Pokémon | MapleStory | Guild Wars 2</p>
			</i>
		</div>
	</div>
{/if}
