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
			<Button
				size="icon"
				variant={selectedTab === 'presskit' ? 'default' : 'outline'}
				class="text-2xl min-w-fit px-3"
				on:click={() => (selectedTab = 'presskit')}>Press Kit</Button
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
				unhoveredImage="gonzalo-episode-1.jpg"
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

<!-- Press Kit tab -->
{#if selectedTab === 'presskit'}
	<div class="press-kit-content">
		<div class="pk-container">
			<aside class="factsheet">
				<h2>Factsheet</h2>

				<div class="fact-block">
					<span class="fact-label">Official Game Title</span>
					<span class="fact-data">Gonzalo the Chicken - Episode I</span>
				</div>

				<div class="fact-block">
					<span class="fact-label">Development Studio</span>
					<span class="fact-data">WhaleplaneStudios LLC</span>
					<span class="fact-data">Based in Maryland, USA</span>
				</div>

				<div class="fact-block">
					<span class="fact-label">Planned Release</span>
					<span class="fact-data">Summer 2026</span>
				</div>

				<div class="fact-block">
					<span class="fact-label">Genre</span>
					<span class="fact-data">Adventure Platformer</span>
				</div>

				<div class="fact-block">
					<span class="fact-label">Platform</span>
					<span class="fact-data">PC</span>
				</div>

				<div class="fact-block">
					<span class="fact-label">Number of Players</span>
					<span class="fact-data">Singleplayer</span>
				</div>

				<div class="fact-block">
					<span class="fact-label">Art Style</span>
					<span class="fact-data">Cartoon Bright Low Poly</span>
				</div>

				<div class="fact-block">
					<span class="fact-label">Steam Page</span>
					<span class="fact-data"
						><a
							href="https://store.steampowered.com/app/4117840/Gonzalo_the_Chicken__Episode_I/"
							target="_blank">Store Link</a
						></span
					>
				</div>

				<div class="fact-block">
					<span class="fact-label">Discord</span>
					<span class="fact-data"
						><a href="https://discord.gg/ggkatrDpmv" target="_blank">Join Discord</a></span
					>
				</div>

				<div class="fact-block">
					<span class="fact-label">Other Social Media</span>
					<span class="fact-data"
						><a href="https://www.instagram.com/whaleplanestudios/" target="_blank">Instagram</a
						></span
					>
					<span class="fact-data"
						><a href="https://www.youtube.com/@whaleplanestudios5293" target="_blank">Youtube</a
						></span
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
				<h2>Gonzalo the Chicken - Episode I</h2>
				<p>
					Gonzalo the Chicken is a single player adventure platformer where you navigate a unique
					world with a mysterious past in the midst of a great war. Use your chatty, retrievable
					bomb companion, Azzar, to fight the Crocogator army. Collect all of Azzar's exciting
					mutations like fire, homing, and sticky in order to solve puzzles and take out a variety
					of strong enemies and challenging bosses. The world's bright, low-poly art style takes
					Gonzalo through wild environments with unique enemies including the crabs of Claw Island
					and the Dryads in the forests of Noxglade. It's time for this chicken to cross the road...
					and blow up everything on the other side!
				</p>

				<h2>Game Description</h2>
				<p>
					You are Gonzalo, flightless and hard-headed, exploring a mysterious world abandoned by an
					ancient creator. Team up with Azzar, a retrievable bomb companion whose firepower makes up
					for all the yapping. Blow up enemies with various bomb mutations, traverse obstacles with
					ridiculous movement mechanics, and fight back against the terrifying Crocogator army. If
					you are worthy, you can get recruited by the Noctuans, a faction of no-nonsense owl
					creatures, who will only allow you to add to your destructive capabilities.
				</p>

				<p>
					Gonzalo is a tough chicken who is not clucking around. If enemies are too close for
					comfort, hit them with a combo or ground pound to push back a full flock of Crocogators.
					Flap your arms to stay in the air a little longer and go a little farther. Dodge and dive
					to get away fast and cross longer gaps. Master these mechanics to carefully explore
					ancient secrets, or not so carefully blast to the finish line and beat the par time in
					each level.
				</p>

				<p>
					As the Crocogators increase in strength and numbers, you will need some more firepower to
					defeat them. Throw Azzar at hordes of nasty enemies by consuming collectible bomb goo
					(that he eats?) to unleash his explosive potential. Feed him mutations like fire, homing,
					and sticky bomb upgrades to solve puzzles, tackle stronger enemies, and even defeat
					bosses. Don't forget to retrieve Azzar after you throw him so you can throw him again for
					limitless destruction... and don't worry, he's into it.
				</p>

				<p>
					Crocogators will rip, tear, bash, shoot, and burn through anything in their way. If you
					can catch a break from those, a menagerie of other deadly creatures like snowmen, crabs,
					and dryads are waiting for you. You think you have what it takes? Good, because there's
					also a series of crazy bosses you must also defeat throughout your journey.
				</p>

				<p>
					If that's not enough, there is still a full plate of collectibles that unlock a variety of
					special abilities for your adventure. Fireworks, pickup magnets, infinite bomb goo...
					squeaky boots? If that sounds enticing, then search for secret eggs in each level and
					collect as many coins as you can. Order everything on our Breakfast Menu to completely
					transform your experience and replay the game with hilarious setting combinations.
				</p>

				<p>
					Are you ready to cause some poultry pandemonium? Gonzalo and Azzar are waiting to blow
					your mind, literally. Get ready to cluck, chuck, and kaboom your way to victory.
				</p>

				<h2>Who is WhaleplaneStudios?</h2>
				<p>
					Jeremy and Jake, the two man team behind WhaleplaneStudios, have been friends since high
					school. Gonzalo the Chicken started as a small hobby project in 2020, but after several
					iterations and reworks, we are excited to finally have this opportunity to publish our
					first complete game. Our friend Anders has composed an incredible soundtrack for the game
					that really brings it to a new level. Jeremy and Jake grew up on games like Jak and Daxter
					and the famous 3D Mario platformers and wanted to create something that starts to echo the
					style of these masterpieces with a fresh take. We may be a small part-time studio, but we
					aspire to make great games that we have fun playing ourselves.
				</p>
				<!--Need to figure out tense here ^ "have been friends" but then immediately "we are excited"-->
				<!--Maybe start with "We are Jeremy Neville and Jake Facius, the two man team..."-->

				<h2>Contact Us</h2>
				<p><a href="mailto:owners@whaleplanestudios.org">owners@whaleplanestudios.org</a></p>
			</main>

			<aside class="media-gallery">
				<h3>Media Gallery</h3>
				<div class="gallery-track">
					<!-- Gameplay Trailer - Embed YouTube video -->
					<div class="gallery-item">
						<iframe
							src="https://www.youtube.com/embed/3fBHZ1C54uI"
							title="Gameplay Trailer"
							frameborder="0"
							allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
							allowfullscreen
							class="media-embed"
						></iframe>
					</div>

					<!-- Screenshots -->
					<div class="gallery-item">
						<a href="presskit/1_ShooterVsBomb.png" download class="gallery-item">
							<img src="presskit/1_ShooterVsBomb.png" alt="Shooter vs Bomb" class="media-image" />
						</a>
					</div>
					<div class="gallery-item">
						<a href="presskit/2_KingCrabClaws.png" download class="gallery-item">
							<img src="presskit/2_KingCrabClaws.png" alt="King Crab Claws" class="media-image" />
						</a>
					</div>
					<div class="gallery-item">
						<a href="presskit/3_Shrug.png" download class="gallery-item">
							<img src="presskit/3_Shrug.png" alt="Shrug" class="media-image" />
						</a>
					</div>
					<div class="gallery-item">
						<a href="presskit/4_Flutter.png" download class="gallery-item">
							<img src="presskit/4_Flutter.png" alt="Flutter" class="media-image" />
						</a>
					</div>
					<div class="gallery-item">
						<a href="presskit/5_Warden.png" download class="gallery-item">
							<img src="presskit/5_Warden.png" alt="Warden" class="media-image" />
						</a>
					</div>
					<div class="gallery-item">
						<a href="presskit/6_Snowman.png" download class="gallery-item">
							<img src="presskit/6_Snowman.png" alt="Snowman" class="media-image" />
						</a>
					</div>
					<div class="gallery-item">
						<a href="presskit/7_SneakAttack.png" download class="gallery-item">
							<img src="presskit/7_SneakAttack.png" alt="Sneak Attack" class="media-image" />
						</a>
					</div>
					<div class="gallery-item">
						<a href="presskit/8_KingCrab.png" download class="gallery-item">
							<img src="presskit/8_KingCrab.png" alt="King Crab" class="media-image" />
						</a>
					</div>
					<div class="gallery-item">
						<a href="presskit/9_SewerRun.png" download class="gallery-item">
							<img src="presskit/9_SewerRun.png" alt="Sewer Run" class="media-image" />
						</a>
					</div>
					<div class="gallery-item">
						<a href="presskit/10_Floaters.png" download class="gallery-item">
							<img src="presskit/10_Floaters.png" alt="Floaters" class="media-image" />
						</a>
					</div>
					<div class="gallery-item">
						<a href="presskit/11_KingCrabBlasted.png" download class="gallery-item">
							<img src="presskit/11_KingCrabBlasted.png" alt="King Crab" class="media-image" />
						</a>
					</div>
					<div class="gallery-item">
						<a href="presskit/12_Checkpoint.png" download class="gallery-item">
							<img src="presskit/12_Checkpoint.png" alt="Checkpoint" class="media-image" />
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

	@media (max-width: 1200px) {
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
