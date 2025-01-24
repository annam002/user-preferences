<svelte:head>
	<title>Motion</title>
</svelte:head>

<div class="text-column">
	<p>
		Motion in websites can make users sick, cause migraines or seizures. Use animations sparingly,
		and make do not run animations when user has preference set to reduce motion.
	</p>

	<p>A beating heart - set reduce motion in your OS settings to stop it</p>

	<div class="p-8">
		<div class="heart"></div>
	</div>

	<h2>Read on</h2>
	<ul>
		<li>
			Link to documentation: <a
				href="https://developer.mozilla.org/en-US/docs/Web/CSS/@media/prefers-reduced-motion"
				>prefers-reduced-motion</a>
		</li>
		<li>
			WCAG criterion 2.2.2: <a href="https://www.w3.org/WAI/WCAG22/quickref/#pause-stop-hide"
				>Pause, Stop, Hide</a>
		</li>
		<li>
			Background reading: <a href="https://alistapart.com/article/accessibility-for-vestibular/"
				>Accessibility for vestibular disorders</a>
		</li>
	</ul>
</div>

<style>
	.heart {
		position: relative;
		width: 80px;
		height: 80px;
		background-color: red;
		transform: rotate(-45deg);
		animation: blink 1s infinite;
		padding: 1rem;
	}

	@media (prefers-reduced-motion: reduce) {
		.heart {
			animation: none;
		}
	}

	.heart::before,
	.heart::after {
		content: '';
		position: absolute;
		width: 80px;
		height: 80px;
		background-color: red;
		border-radius: 50%;
	}

	.heart::before {
		top: -50px;
		left: 0;
	}

	.heart::after {
		left: 50px;
		top: 0;
	}

	@keyframes blink {
		0%,
		100% {
			opacity: 1;
		}
		50% {
			opacity: 0;
		}
	}
</style>
