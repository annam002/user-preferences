<svelte:head>
	<title>Forced Colors</title>
</svelte:head>

<div class="text-column">
	<p>
		When forced-colors is active, your entire website colors are overwritten with colors specified
		by the user.
	</p>
	<p>This can be triggered as follows:</p>
	<ul>
		<li>On Windows and Ubuntu: Turn on high-contrast mode</li>
		<li>On MacOS this can be turned on in Firefox in the settings</li>
		<li>For simulation, you can toggle forced-colors in the rendering pane in Chrome.</li>
	</ul>
	<p>Forced-colors overwrites it all, but you need to pay attention to some gotchas.</p>
	<ul class="flex flex-col gap-2">
		<li class="item-with-shadow">
			Shadows are gone. So if you use a shadow as differentiator you need to replace it.
		</li>
		<li class="item-with-background">
			All background colors are converged into one. If you use different background colors to
			separate elements, you need to use an outline instead.
		</li>
		<li>
			<p>If colours are used to convey meaning, this will no longer work. Add another indicator.</p>
			<div class="flex items-center gap-4">
				<div class="flex flex-col gap-2 border border-gray-500 p-4">
					<em class="text-xl">Don't do this!</em>
					<p>
						Availability: <span class="indicator"></span>
					</p>
				</div>
				<div class="flex flex-col gap-2 border border-gray-500 p-4">
					<em class="text-xl">Do this!</em>
					<p>
						Availability: low <span class="indicator"></span>
					</p>
				</div>
			</div>
		</li>
	</ul>
	<p></p>
	<p>
		Link to documentation: <a
			href="https://developer.mozilla.org/en-US/docs/Web/CSS/@media/forced-colors">forced-colors</a>
	</p>
</div>

<style>
	.item-with-shadow {
		box-shadow:
			-2px -2px 5px green,
			2px 2px 5px green;
	}

	.item-with-background {
		background-color: #ddccaa;
	}

	.indicator {
		border: 1px solid red;
		background-color: red;
		display: inline-block;
		border-radius: 50%;
		height: 20px;
		width: 20px;
	}

	@media (forced-colors: active) {
		.item-with-shadow,
		.item-with-background {
			border: 1px solid ButtonBorder;
		}
	}
</style>
