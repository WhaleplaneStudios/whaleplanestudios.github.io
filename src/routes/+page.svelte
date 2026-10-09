<script lang="ts">
	import GameHoverButton from '$lib/components/game-hover-button.svelte';
	import SocialMediaTooltipButton from '$lib/components/social-media-tooltip-button.svelte';
	import { Button } from '$lib/components/ui/button/index.js';
	import { onMount } from 'svelte';

	let innerWidth = 0;
	let innerHeight = 0;
	let selectedTab = 'games';

	$: isScreenPortrait = innerWidth * 1.33 <= innerHeight;

	// Function to handle tab changes and update hash
	function changeTab(tab: string) {
		selectedTab = tab;
		window.location.hash = tab === 'games' ? '' : tab;
	}

	// Read hash on mount and when hash changes
	function updateTabFromHash() {
		const hash = window.location.hash.slice(1); // Remove the '#'
		if (hash === 'team' || hash === 'presskit') {
			selectedTab = hash;
		} else {
			selectedTab = 'games';
		}
	}

	onMount(() => {
		updateTabFromHash();
		window.addEventListener('hashchange', updateTabFromHash);
		return () => window.removeEventListener('hashchange', updateTabFromHash);
	});
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
				on:click={() => changeTab('games')}>Our Games</Button
			>
			<Button
				size="icon"
				variant={selectedTab === 'team' ? 'default' : 'outline'}
				class="text-2xl min-w-fit px-3"
				on:click={() => changeTab('team')}>Our Team</Button
			>
			<Button
				size="icon"
				variant={selectedTab === 'presskit' ? 'default' : 'outline'}
				class="text-2xl min-w-fit px-3"
				on:click={() => changeTab('presskit')}>Press Kit</Button
			>
		</div>
		<!-- Social media links -->
		<div class="justify-self-center lg:justify-self-end space-x-2">
			<SocialMediaTooltipButton
				link="https://store.steampowered.com/app/4117840/Gonzalo_the_Chicken/"
				tooltipText="Wishlist on Steam!"
				icon="mdi:steam"
			/>
			<SocialMediaTooltipButton
				link="https://discord.gg/ggkatrDpmv"
				tooltipText="Chat with us on Discord!"
				icon="ic:baseline-discord"
			/>
			<SocialMediaTooltipButton
				link="https://www.instagram.com/whaleplanestudios/"
				tooltipText="Follow us on Instagram!"
				icon="ri:instagram-fill"
			/>
			<SocialMediaTooltipButton
				link="https://www.youtube.com/channel/UCSk-EZSzULqEszKrE2j361Q"
				tooltipText="Watch our videos on YouTube!"
				icon="mdi:youtube"
			/>
			<SocialMediaTooltipButton
				link="https://www.tiktok.com/@whaleplanestudios"
				tooltipText="Follow us on TikTok!"
				icon="ic:baseline-tiktok"
			/>
			<SocialMediaTooltipButton
				link="https://x.com/Whaleplane"
				tooltipText="Follow us on X!"
				icon="fa7-brands:x-twitter"
			/>
			<SocialMediaTooltipButton
				link="https://bsky.app/profile/whaleplanestudios.bsky.social"
				tooltipText="Follow us on Bluesky!"
				icon="mdi:cloud"
			/>
			<SocialMediaTooltipButton
				link="https://www.threads.net/@whaleplanestudios"
				tooltipText="Follow us on Threads!"
				icon="mdi:at"
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
				altText="Gonzalo the Chicken"
				hoveredImage="gonzalo-hovered.png"
				unhoveredImage="gonzalo.png"
				link="https://store.steampowered.com/app/4117840/Gonzalo_the_Chicken/"
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

<!-- Press Kit tab -->
{#if selectedTab === 'presskit'}
	<div class="press-kit-content">
		<div class="pk-container">
			<aside class="factsheet">
				<h2>Press Kit</h2>
				<span class="fact-data"
					><a
						href="https://drive.google.com/drive/folders/1VVSluDB3tAIIx4Zm4pbwGR9HKF3ZKJ10?usp=drive_link"
						target="_blank">Google Drive</a
					></span
				>
				<span class="fact-data"
					><a
						href="https://drive.usercontent.google.com/download?id=1-hDuKO3fyGTc0EIiIs2izLDAiTnz7ulH&export=download&authuser=0"
						target="_blank">Download as .zip</a
					></span
				>
				<br />

				<h2>Factsheet</h2>

				<div class="fact-block">
					<span class="fact-label">Official Game Title</span>
					<span class="fact-data">Gonzalo the Chicken</span>
				</div>

				<div class="fact-block">
					<span class="fact-label">Development Studio</span>
					<span class="fact-data">WhaleplaneStudios LLC</span>
					<span class="fact-data">Based in Maryland, USA</span>
				</div>

				<div class="fact-block">
					<span class="fact-label">Planned Release</span>
					<span class="fact-data">Early 2027</span>
				</div>

				<div class="fact-block">
					<span class="fact-label">Genre</span>
					<span class="fact-data">Action-Adventure Platformer</span>
				</div>

				<div class="fact-block">
					<span class="fact-label">Platform</span>
					<span class="fact-data">PC | Steam Deck/SteamOS | Linux</span>
				</div>

				<div class="fact-block">
					<span class="fact-label">Number of Players</span>
					<span class="fact-data">Singleplayer</span>
				</div>

				<div class="fact-block">
					<span class="fact-label">Art Style</span>
					<span class="fact-data">Stylized | Low Poly <br /> Pixel Art Textures</span>
				</div>

				<div class="fact-block">
					<span class="fact-label">Steam Store Pages</span>
					<span class="fact-data"
						><a
							href="https://store.steampowered.com/app/4117840/Gonzalo_the_Chicken/"
							target="_blank">Gonzalo the Chicken</a
						>
						<br />
						<a
							href="https://store.steampowered.com/app/5226990/Gonzalo_the_Chicken_Demo/"
							target="_blank">Gonzalo the Chicken Demo</a
						></span
					>
				</div>

				<div class="fact-block">
					<span class="fact-label">Discord</span>
					<span class="fact-data"
						><a href="https://discord.gg/ggkatrDpmv" target="_blank">Join Our Discord</a></span
					>
				</div>

				<div class="fact-block">
					<span class="fact-label">Other Social Media</span>
					<span class="fact-data"
						><a href="https://www.instagram.com/whaleplanestudios/" target="_blank">Instagram</a
						></span
					>
					<span class="fact-data"
						><a href="https://www.youtube.com/@whaleplanestudios" target="_blank">Youtube</a></span
					>
					<span class="fact-data"
						><a href="https://www.tiktok.com/@whaleplanestudios" target="_blank">TikTok</a></span
					>
					<span class="fact-data"><a href="https://x.com/Whaleplane" target="_blank">X</a></span>
					<span class="fact-data"
						><a href="https://bsky.app/profile/whaleplanestudios.bsky.social" target="_blank"
							>Bluesky</a
						></span
					>
					<span class="fact-data"
						><a href="https://www.threads.com/@whaleplanestudios" target="_blank">Threads</a></span
					>
					<span class="fact-data"
						><a href="https://www.facebook.com/WhaleplaneStudios" target="_blank">Facebook</a></span
					>
				</div>
			</aside>

			<main class="pk-content">
				<div class="presskit-banner mb-4">
					<img src="presskit/Banner_1200x400.png" alt="Press Kit Banner" class="w-full rounded" />
				</div>
				<p>
					This chicken is crossing the road... to blow up everything on the other side! Throw
					Gonzalo's loud-mouthed explosive sidekick Azzar at the Crocogator horde, and then use a
					magic glove to retrieve him. He holds on tight while you flutter through mountains and
					beaches and forests, oh my!
				</p>
				<div class="grid grid-cols-2 md:grid-cols-4 gap-4 mb-6">
					<a
						href="presskit/1_jumpdodge.gif"
						download
						class="block rounded overflow-hidden bg-black"
					>
						<img
							src="presskit/1_jumpdodge.gif"
							alt="Bomb throw GIF"
							class="w-full h-full object-cover"
						/>
					</a>
					<a
						href="presskit/2_bombthrow.gif"
						download
						class="block rounded overflow-hidden bg-black"
					>
						<img
							src="presskit/2_bombthrow.gif"
							alt="Crab dodge GIF"
							class="w-full h-full object-cover"
						/>
					</a>
					<a href="presskit/3_kickcroc.gif" download class="block rounded overflow-hidden bg-black">
						<img
							src="presskit/3_kickcroc.gif"
							alt="Platforms GIF"
							class="w-full h-full object-cover"
						/>
					</a>
					<a
						href="presskit/4_crumblingplatforms.gif"
						download
						class="block rounded overflow-hidden bg-black"
					>
						<img
							src="presskit/4_crumblingplatforms.gif"
							alt="Kicking Crocs GIF"
							class="w-full h-full object-cover"
						/>
					</a>
				</div>
				<h2>Game Description</h2>
				<p><strong>Endless Explosions</strong></p>
				<p>
					Throw your retrievable bomb companion Azzar at hordes of nasty enemies by consuming
					collectible bomb goo (that he eats?) to unleash his explosive potential. Retrieve Azzar
					after you throw him so you can throw him again for limitless destruction... and don&#39;t
					worry, he&#39;s into it. His devastating firepower tries to make up for all the yapping
					while you explore this mysterious world abandoned by an ancient creator. Experiment by
					blowing up even more enemies with various bomb mutations like fire, homing, and sticky
					bomb upgrades, and then leverage them to solve puzzles, take out stronger enemies, and
					even exploit boss weaknesses.
				</p>
				<p><strong>Poultry Power</strong></p>
				<p>
					You play as Gonzalo: flightless, hard-headed, and stuck with Azzar for now, but this
					chicken does not cluck around! If enemies are too close for comfort, hit them with a combo
					or ground pound to push back a full flock of Crocogators. Flap your arms to stay in the
					air a little longer and go a little farther. Use your dodge and air dive to get away fast,
					cross longer gaps, or traverse obstacles that require ridiculous movement chains. Master
					these mechanics to carefully explore ancient secrets, but don&#39;t forget to
					not-so-carefully use Azzar if you need to blast through obstacles to get to the finish
					line and beat the par time in each level.
				</p>
				<p><strong>Fearsome Feather Fodder Foes</strong></p>
				<p>
					They made fried chicken out of your family, so you must fight back against the relentless
					Crocogator army. They rip, tear, bash, shoot, and burn through anything in their way. If
					you can catch a break from them, a menagerie of other deadly creatures like snowmen,
					crabs, and dryads are waiting for you. You think you have what it takes? Good, because
					there&#39;s also a lineup of monstrous bosses waiting to test your limits.
				</p>
				<p><strong>Shiny Stuff &amp; Squeaky Secrets</strong></p>
				<p>
					Search for secret eggs in each level and collect as many coins as you can to unlock
					fireworks, pickup magnets, infinite bomb goo, and... squeaky boots? Order everything on
					our Breakfast Menu to completely transform your experience and replay the game with
					hilarious setting combinations and unstoppable bomb mutations.
				</p>
				<p>
					Ready to cause some poultry pandemonium? Gonzalo and Azzar are waiting to blow your mind,
					literally. Get ready to cluck, chuck, and kaboom your way to victory!
				</p>

				<h2>About WhaleplaneStudios</h2>
				<p>
					We are Jeremy and Jake, the two man team behind WhaleplaneStudios, and we have been
					friends since high school. Gonzalo the Chicken started as a small hobby project in 2020,
					but after several iterations and reworks, we are excited to finally have this opportunity
					to publish our first complete game. We have always aspired to make great games that we
					have fun playing ourselves, and we've had a blast with Gonzalo the Chicken. Our friend
					Anders has composed an incredible soundtrack for the game that really brings it to a new
					level. We grew up on games like Jak and Daxter and the famous 3D Mario platformers and
					wanted to create something that starts to echo the style of these masterpieces with a
					fresh take.
				</p>

				<h2>Contact Us</h2>
				<p><a href="mailto:owners@whaleplanestudios.org">owners@whaleplanestudios.org</a></p>
				<br />
				<span class="fact-data"
					><a
						href="https://drive.google.com/drive/folders/1VVSluDB3tAIIx4Zm4pbwGR9HKF3ZKJ10?usp=drive_link"
						target="_blank">Google Drive</a
					></span
				>
				<span class="fact-data"
					><a
						href="https://drive.usercontent.google.com/download?id=1-hDuKO3fyGTc0EIiIs2izLDAiTnz7ulH&export=download&authuser=0"
						target="_blank">Download as .zip</a
					></span
				>
			</main>

			<aside class="media-gallery">
				<h3>Media Gallery</h3>
				<div class="gallery-track">
					<!-- Gameplay Trailer - Embed YouTube video -->
					<div class="gallery-item">
						<iframe
							src="https://www.youtube.com/embed/DW0byoiK5UY"
							title="Gameplay Trailer"
							frameborder="0"
							allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
							allowfullscreen
							class="media-embed"
						></iframe>
					</div>

					<!-- Screenshots -->
					<div class="gallery-item">
						<a href="presskit/ApproachingShip.png" download class="gallery-item">
							<img src="presskit/ApproachingShip.png" alt="Approaching Ship" class="media-image" />
						</a>
					</div>
					<div class="gallery-item">
						<a href="presskit/SmokeTrails.png" download class="gallery-item">
							<img src="presskit/SmokeTrails.png" alt="Smoke Trails" class="media-image" />
						</a>
					</div>
					<div class="gallery-item">
						<a href="presskit/CrocExplosion.png" download class="gallery-item">
							<img src="presskit/CrocExplosion.png" alt="Croc Explosion" class="media-image" />
						</a>
					</div>
					<div class="gallery-item">
						<a href="presskit/Retrieval.png" download class="gallery-item">
							<img src="presskit/Retrieval.png" alt="Retrieval" class="media-image" />
						</a>
					</div>
					<div class="gallery-item">
						<a href="presskit/Flutter.png" download class="gallery-item">
							<img src="presskit/Flutter.png" alt="Flutter" class="media-image" />
						</a>
					</div>
					<div class="gallery-item">
						<a href="presskit/ShieldKick.png" download class="gallery-item">
							<img src="presskit/ShieldKick.png" alt="Shield Kick" class="media-image" />
						</a>
					</div>
					<div class="gallery-item">
						<a href="presskit/Warden.png" download class="gallery-item">
							<img src="presskit/Warden.png" alt="Warden" class="media-image" />
						</a>
					</div>
					<div class="gallery-item">
						<a href="presskit/KeyDoor.png" download class="gallery-item">
							<img src="presskit/KeyDoor.png" alt="Key Door" class="media-image" />
						</a>
					</div>
					<div class="gallery-item">
						<a href="presskit/YetiFire.png" download class="gallery-item">
							<img src="presskit/YetiFire.png" alt="Yeti Fire" class="media-image" />
						</a>
					</div>
					<div class="gallery-item">
						<a href="presskit/CrocArmy.png" download class="gallery-item">
							<img src="presskit/CrocArmy.png" alt="Croc Army" class="media-image" />
						</a>
					</div>
					<div class="gallery-item">
						<a href="presskit/ShooterMissed.png" download class="gallery-item">
							<img src="presskit/ShooterMissed.png" alt="Shooter Missed" class="media-image" />
						</a>
					</div>
					<div class="gallery-item">
						<a href="presskit/FireRetrieval.png" download class="gallery-item">
							<img src="presskit/FireRetrieval.png" alt="Fire Retrieval" class="media-image" />
						</a>
					</div>
					<div class="gallery-item">
						<a href="presskit/SnowmanKick.png" download class="gallery-item">
							<img src="presskit/SnowmanKick.png" alt="Snowman Kick" class="media-image" />
						</a>
					</div>
					<div class="gallery-item">
						<a href="presskit/Spoons.png" download class="gallery-item">
							<img src="presskit/Spoons.png" alt="Spoons" class="media-image" />
						</a>
					</div>
					<div class="gallery-item">
						<a href="presskit/Helicrocter.png" download class="gallery-item">
							<img src="presskit/Helicrocter.png" alt="Helicrocter" class="media-image" />
						</a>
					</div>
					<div class="gallery-item">
						<a href="presskit/SadSnowman.png" download class="gallery-item">
							<img src="presskit/SadSnowman.png" alt="SadSnowman" class="media-image" />
						</a>
					</div>
				</div>
			</aside>
		</div>
	</div>
{/if}

<style>
	/* Press Kit specific styles */
	.press-kit-content {
		background-color: #1a1a1a;
		color: #e0e0e0;
	}

	.press-kit-content a {
		color: #ff8c42;
		text-decoration: none;
		font-weight: bold;
	}

	.press-kit-content a:hover {
		text-decoration: underline;
		color: #ffa666;
	}

	.pk-container {
		display: flex;
		margin: 40px auto;
		padding: 0 20px;
		gap: 40px;
	}

	.factsheet {
		flex: 0 0 300px;
		position: -webkit-sticky;
		position: sticky;
		top: 20px;
		align-self: flex-start;
		background: #2a2a2a;
		padding: 20px;
		border-radius: 8px;
		box-shadow: 0 2px 10px rgba(0, 0, 0, 0.3);
		max-height: 90vh;
		overflow-y: auto;
		color: #333;
	}

	.factsheet h2 {
		margin-bottom: 20px;
		font-size: 1.5rem;
		border-bottom: 2px solid #444;
		padding-bottom: 10px;
		color: #fff;
	}

	.fact-block {
		margin-bottom: 20px;
	}

	.fact-label {
		font-weight: bold;
		display: block;
		color: #aaa;
		font-size: 0.9rem;
		text-transform: uppercase;
	}

	.fact-data {
		margin-bottom: 5px;
		display: block;
		color: #e0e0e0;
	}

	.pk-content {
		flex: 0 0 1200px;
		background: #2a2a2a;
		padding: 40px;
		border-radius: 8px;
		box-shadow: 0 2px 10px rgba(0, 0, 0, 0.3);
		color: #e0e0e0;
	}

	.pk-content h2 {
		margin-top: 30px;
		margin-bottom: 15px;
		color: #fff;
		font-size: 2.2rem;
		border-bottom: 1px solid #444;
		padding-bottom: 10px;
	}

	.pk-content h2:first-of-type {
		margin-top: 0;
	}

	.pk-content p {
		margin-bottom: 15px;
		line-height: 1.8;
		font-size: 1.1rem;
	}

	.media-gallery {
		flex: 1;
		min-width: 350px;
		position: -webkit-sticky;
		position: sticky;
		top: 20px;
		align-self: flex-start;
		background: #2a2a2a;
		padding: 20px;
		border-radius: 8px;
		box-shadow: 0 2px 10px rgba(0, 0, 0, 0.3);
		max-height: 90vh;
		overflow-y: hidden;
	}

	.media-gallery h3 {
		margin-bottom: 20px;
		font-size: 1.5rem;
		color: #fff;
		border-bottom: 2px solid #444;
		padding-bottom: 10px;
	}

	.gallery-track {
		display: flex;
		flex-direction: column;
		gap: 20px;
		overflow-y: auto;
		max-height: calc(90vh - 100px);
		padding-right: 10px;
		-webkit-overflow-scrolling: touch;
	}

	.gallery-track::-webkit-scrollbar {
		width: 8px;
	}
	.gallery-track::-webkit-scrollbar-track {
		background: #333;
		border-radius: 4px;
	}
	.gallery-track::-webkit-scrollbar-thumb {
		background: #ff8c42;
		border-radius: 4px;
		border: 2px solid #333;
	}

	.gallery-item {
		flex: 0 0 auto;
		width: 100%;
		max-width: 1200px;
		aspect-ratio: 16/9;
		background-color: #444;
		border-radius: 8px;
		overflow: hidden;
		display: flex;
		align-items: center;
		justify-content: center;
		position: relative;
	}

	.placeholder-text {
		color: #aaa;
		font-weight: bold;
	}

	.media-image {
		width: 100%;
		height: 100%;
		object-fit: cover;
		display: block;
	}

	.media-embed {
		width: 100%;
		height: 100%;
		border: none;
	}

	/* Tweak layout specifically for common 1920x1080 displays so it visually matches 2560x1440
       but slightly smaller to fit everything. Does not affect mobile (<=1200px) or larger 2560px+ */
	@media (min-width: 1500px) and (max-width: 1920px) {
		.pk-container {
			gap: 24px;
			margin: 32px auto;
			padding: 0 16px;
		}

		.factsheet {
			flex: 0 0 260px;
			padding: 16px;
			max-height: 85vh;
		}

		.factsheet h2 {
			font-size: 1.35rem;
		}

		.pk-content {
			flex: 0 0 1000px;
			padding: 30px;
		}

		.pk-content h2 {
			font-size: 2rem;
		}

		.pk-content p {
			font-size: 1.03rem;
		}

		.media-gallery {
			min-width: 320px;
			padding: 16px;
			max-height: 85vh;
		}

		.gallery-track {
			gap: 16px;
			max-height: calc(85vh - 80px);
		}

		.gallery-item {
			max-width: 1000px;
		}
	}

	@media (max-width: 900px) {
		.pk-container {
			flex-direction: column;
		}
		.factsheet,
		.media-gallery {
			flex: none;
			width: 100%;
			position: relative;
			top: 0;
			max-height: none;
		}
		.gallery-track {
			flex-direction: row;
			overflow-x: auto;
			overflow-y: hidden;
			max-height: none;
			padding-bottom: 20px;
			padding-right: 0;
		}
		.gallery-track::-webkit-scrollbar {
			height: 12px;
			width: auto;
		}
		.gallery-item {
			width: 85vw;
			flex-shrink: 0;
		}
	}
</style>
