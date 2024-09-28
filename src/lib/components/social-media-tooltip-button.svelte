<script lang="ts">
	import { Button } from '$lib/components/ui/button/index.js';
	import IconifyIcon from '@iconify/svelte';
	import * as Tooltip from './ui/tooltip';

	export let link;
	export let tooltipText;
	export let icon;
</script>

<Tooltip.Root openDelay={50}>
	<Tooltip.Trigger asChild let:builder>
		<Button builders={[builder]} href={link} size="icon" variant="outline" target="_blank">
			<IconifyIcon class="w-8 h-8 lg:w-14 lg:h-14" {icon} />
		</Button>
	</Tooltip.Trigger>
	<Tooltip.Content>
		<p>{tooltipText}</p>
	</Tooltip.Content>
</Tooltip.Root>
