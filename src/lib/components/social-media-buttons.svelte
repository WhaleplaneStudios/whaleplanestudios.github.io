<script lang="ts">
	import { Button } from '$lib/components/ui/button/index.js';
	import IconifyIcon from '@iconify/svelte';

	$: socialMediaHoverText = '';
</script>

<!-- Social media buttons, each with hover text changing -->
<div class="flex justify-center space-x-6 mt-6">
	<Button
		href="https://discord.gg/ggkatrDpmv"
		size="icon"
		on:mouseenter={() => {
			socialMediaHoverText = 'Chat with us on Discord!';
		}}
		on:mouseleave={() => {
			socialMediaHoverText = '';
		}}
	>
		<IconifyIcon class="w-14 h-14" icon="ic:baseline-discord" />
	</Button>

	<Button
		href="https://whaleplanestudios.itch.io/"
		size="icon"
		on:mouseenter={() => {
			socialMediaHoverText = 'Play our games on itch.io!';
		}}
		on:mouseleave={() => {
			socialMediaHoverText = '';
		}}
	>
		<IconifyIcon class="w-12 h-12" icon="cib:itch-io" />
	</Button>

	<Button
		href="https://www.youtube.com/channel/UCSk-EZSzULqEszKrE2j361Q"
		size="icon"
		on:mouseenter={() => {
			socialMediaHoverText = 'Watch our videos on YouTube!';
		}}
		on:mouseleave={() => {
			socialMediaHoverText = '';
		}}
	>
		<IconifyIcon class="w-14 h-14" icon="mdi:youtube" />
	</Button>

	<Button
		href="https://www.facebook.com/WhaleplaneStudios"
		size="icon"
		on:mouseenter={() => {
			socialMediaHoverText = 'Like us on Facebook!';
		}}
		on:mouseleave={() => {
			socialMediaHoverText = '';
		}}
	>
		<IconifyIcon class="w-14 h-14" icon="ic:baseline-facebook" />
	</Button>

	<Button
		href="https://www.instagram.com/whaleplanestudios/"
		size="icon"
		on:mouseenter={() => {
			socialMediaHoverText = 'Follow us on Instagram!';
		}}
		on:mouseleave={() => {
			socialMediaHoverText = '';
		}}
	>
		<IconifyIcon class="w-14 h-14" icon="ri:instagram-fill" />
	</Button>
</div>

<!-- Text to change on each hover -->
<div class="flex justify-center mt-6 text-lg">
	{socialMediaHoverText}
</div>
