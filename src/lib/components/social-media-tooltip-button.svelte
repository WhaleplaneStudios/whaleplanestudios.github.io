<script lang="ts">
	import { Button } from '$lib/components/ui/button/index.js';
	import IconifyIcon from '@iconify/svelte';
	import * as Tooltip from './ui/tooltip';

	export let link;
	export let tooltipText;
	export let icon;
	export let iconClass = 'w-14 h-14';
</script>

<Tooltip.Root openDelay={50}>
	<Tooltip.Trigger asChild let:builder>
		<Button builders={[builder]} href={link} size="icon" variant="outline">
			<IconifyIcon class={iconClass} {icon} />
		</Button>
	</Tooltip.Trigger>
	<Tooltip.Content>
		<p>{tooltipText}</p>
	</Tooltip.Content>
</Tooltip.Root>
