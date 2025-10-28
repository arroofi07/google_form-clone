<script lang="ts">
	import logo from '$lib/assets/logo.png';
	import * as HoverCard from '$lib/components/ui/hover-card/index.js';
	import { Button } from '$lib/components/ui/button/index.js';
	import { Eye, Palette, Undo2, Redo2 } from '@lucide/svelte';
	import * as Avatar from '$lib/components/ui/avatar/index.js';

	// list menu items
	const itemMenu = [
		{ label: Palette, href: '/profile', info: 'Tema' },
		{ label: Eye, href: '/settings', info: 'Preview' },
		{ label: Undo2, href: '/logout', info: 'Undo' },
		{ label: Redo2, href: '/logout', info: 'Redo' },
		{ label: 'Publikasikan', href: '/logout', info: 'Simpan' }
	];
</script>

<div class="flex h-28 w-full items-start justify-end-safe gap-4 bg-white px-4 pt-5 pr-12 outline-1">
	<!-- title -->
    <h1 class="absolute top-6 left-8 gap-3 flex justify-between text-center items-center font-serif text-2xl font-semibold text-gray-700">
      <img src={logo} class="w-16 h-16" alt="Logo" />
      Formulir tanpa judul
		</h1>

	<!-- menu -->
	{#each itemMenu as item}
		<HoverCard.Root openDelay={100} closeDelay={100}>
			<HoverCard.Trigger class="">
				<Button
					variant="outline"
					class="cursor-pointer {item.label == 'Publikasikan'
						? 'bg-blue-500 text-white '
						: ''}   hover:bg-gray-100"
				>
					{#if typeof item.label === 'string'}
						<span class="font-serif text-[17px]">{item.label}</span>
					{:else}
						<svelte:component this={item.label} class="text-[17px] " />
					{/if}
				</Button>
			</HoverCard.Trigger>
			<HoverCard.Content
				class=" flex w-auto items-center justify-center rounded-[4px] bg-gray-500 p-1 pr-3 pl-3 text-center font-sans text-[11px] text-white  "
				>{item.info}</HoverCard.Content
			>
		</HoverCard.Root>
	{/each}

	<!-- avatar -->
	<Avatar.Root class="h-10 w-10">
		<Avatar.Image src="https://github.com/shadcn.png" alt="@shadcn" />
		<Avatar.Fallback>CN</Avatar.Fallback>
	</Avatar.Root>
</div>
