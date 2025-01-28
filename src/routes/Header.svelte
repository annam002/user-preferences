<script lang="ts">
	import { page } from '$app/stores';
	import { tick } from 'svelte';
	let menuParent;
	const navItems = [
		{ path: '/', label: 'Home' },
		{ path: '/prefers-color-scheme', label: 'Prefers Color Scheme' },
		{ path: '/color-scheme', label: 'Color Scheme' },
		{ path: '/light-dark', label: 'Light-Dark' },
		{ path: '/system-colors', label: 'System Colors' },
		{ path: '/forced-colors', label: 'Forced Colors' }
		//	{ path: '/motion', label: 'Motion' }
	];
	const currentNavItem = $derived(navItems.filter((i) => $page.url.pathname === i.path)[0]);
	let selectedNavItem = $state(0);
	let menuExpanded = $state(false);
	const toggleMenu = () => {
		menuExpanded = !menuExpanded;
		tick().then(() => {
			if (menuExpanded && menuParent !== undefined) {
				selectedNavItem = 0;
				menuParent.getElementsByTagName('a').item(0).focus();
			}
		});
	};
	page.subscribe(() => {
		menuExpanded = false;
	});

	const focusElement = (id: string) => {
		const element = document.getElementById(id);
		if (element) {
			element.focus();
		}
	};

	const handleKeyDown = (event: KeyboardEvent) => {
		switch (event.key) {
			case 'Up':
			case 'ArrowUp':
			case 'Left':
			case 'ArrowLeft':
				selectedNavItem = selectedNavItem === 0 ? navItems.length - 1 : selectedNavItem - 1;
				focusElement('navitem-' + selectedNavItem);
				event.stopPropagation();
				event.preventDefault();
				return;

			case 'Down':
			case 'ArrowDown':
			case 'Right':
			case 'ArrowRight':
				selectedNavItem = selectedNavItem === navItems.length - 1 ? 0 : selectedNavItem + 1;
				focusElement('navitem-' + selectedNavItem);
				event.stopPropagation();
				event.preventDefault();
				return;
			case 'Escape':
				menuExpanded = false;
				focusElement('menubutton');
				event.stopPropagation();
				event.preventDefault();
				return;
		}
	};
</script>

<header class="flex flex-row items-center gap-8 px-4 lg:flex-col lg:justify-center">
	<nav class="flex">
		<div class="block lg:hidden" bind:this={menuParent}>
			<button
				type="button"
				id="menubutton"
				onclick={() => toggleMenu()}
				aria-haspopup="true"
				aria-controls="menu"
				aria-expanded={menuExpanded}
				aria-label="Menu">
				<svg
					class="menubutton-icon"
					xmlns="http://www.w3.org/2000/svg"
					viewBox="0 0 48 48"
					height="48"
					width="48"
					aria-hidden="true">
					<g>
						<path
							d="M3 5h42s2 0 2 2v2s0 2 -2 2h-42s-2 0 -2 -2v-2s0 -2 2 -2"
							fill="currentColor"
							stroke-width="2"></path>
						<path
							d="M3 21h42s2 0 2 2v2s0 2 -2 2h-42s-2 0 -2 -2v-2s0 -2 2 -2"
							fill="currentColor"
							stroke-width="2"></path>
						<path
							d="M3 37h42s2 0 2 2v2s0 2 -2 2h-42s-2 0 -2 -2v-2s0 -2 2 -2"
							fill="currentColor"
							stroke-width="2"></path>
					</g>
				</svg></button>
			{#if menuExpanded}
				<ul
					id="menu"
					role="menu"
					aria-labelledby="menubutton"
					onkeydown={(event) => handleKeyDown(event)}>
					{#each navItems as navItem, index}
						<li role="none">
							<a
								id={`navitem-${index}`}
								aria-current={currentNavItem.path === navItem.path ? 'page' : undefined}
								role="menuitem"
								href={navItem.path}>{navItem.label}</a>
						</li>
					{/each}
				</ul>
			{/if}
		</div>
		<div class="hidden lg:flex">
			<svg class="nav-decoration" viewBox="0 0 2 3" aria-hidden="true">
				<path d="M0,0 L1,2 C1.5,3 1.5,3 2,3 L2,0 Z" />
			</svg>
			<ul class="horizontal-menu">
				{#each navItems as navItem}
					<li aria-current={currentNavItem.path === navItem.path ? 'page' : undefined}>
						<a href={navItem.path}>{navItem.label}</a>
					</li>
				{/each}
			</ul>
			<svg class="nav-decoration" viewBox="0 0 2 3" aria-hidden="true">
				<path d="M0,0 L0,3 C0.5,3 0.5,3 1,2 L2,0 Z" />
			</svg>
		</div>
	</nav>
	<h1>{currentNavItem.label}</h1>
</header>

<style>
	nav {
		--background: light-dark(var(--color-bg-0), var(--color-bg-dark));
	}

	.nav-decoration {
		width: 2em;
		height: 3em;
		display: block;
	}

	.nav-decoration path {
		fill: var(--background);
	}

	#menu {
		list-style: none;
		border: 1px solid light-dark(black, white);
		position: absolute;
		background: var(--background);
		display: flex;
		flex-direction: column;
		gap: 1rem;
		padding: 0.5rem;
	}

	#menu a {
		text-decoration: none;
	}

	.menubutton-icon {
		color: CanvasText;
		width: 1.5rem;
		height: 1.5rem;
	}

	.horizontal-menu {
		position: relative;
		padding: 0;
		margin: 0;
		height: 3em;
		display: flex;
		justify-content: center;
		align-items: center;
		list-style: none;
		background: var(--background);
		background-size: contain;
	}

	.horizontal-menu li {
		position: relative;
		height: 100%;
	}

	.horizontal-menu li[aria-current='page'],
	#menu a[aria-current='page'] {
		text-decoration: underline;
		text-decoration-color: light-dark(var(--color-text), var(--color-bg));
	}

	.horizontal-menu a {
		display: flex;
		height: 100%;
		align-items: center;
		padding: 0 0.5rem;
		color: light-dark(var(--color-text), var(--color-bg));
		font-weight: 700;
		font-size: 1rem;
		letter-spacing: 0.1em;
		text-decoration: none;
		transition: color 0.2s linear;
	}

	a:hover,
	#menu a:hover {
		color: light-dark(var(--color-theme-1), var(--color-theme-4));
		text-decoration: underline;
	}

	@media (forced-colors: active) {
		.nav-decoration {
			display: none;
		}
	}
</style>
