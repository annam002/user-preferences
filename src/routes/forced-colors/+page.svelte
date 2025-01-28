<script>
	const buttonFocusStyle = `button:focus-visible {<br>
&nbsp;&nbsp;outline: 3px solid black;<br>
&nbsp;&nbsp;box-shadow: 0 0 0 6px white;<br>
}<br>
@media (forced-colors: active) {<br>
&nbsp;&nbsp;button:focus-visible {<br>
&nbsp;&nbsp;&nbsp;outline: 3px solid CanvasText;<br>
&nbsp;}<br>
}`;
</script>

<svelte:head>
	<title>Forced Colors</title>
</svelte:head>

<div class="text-column">
	<p>
		When forced-colors is active, your entire website colors are overwritten with colors specified
		by the user.
	</p>
	<p>
		There is only color for backgrounds, texts links and so on. The colors depend on the OS settings
		and the browser.
	</p>
	<p>
		Check the <a href="/system-colors">system colors page</a> to see which colors are currently effective.
	</p>
	<h2>Enabling forced colors mode</h2>
	<ul>
		<li>On Windows and Ubuntu: Turn on high-contrast mode</li>
		<li>
			On MacOS it is not natively supported. <br />
			If you use Firefox, you can turn this on in the settings (search for "Colours").
			<br />
			If you use Chrome, you can emulate forced-colors on the rendering pane in the developer tools.
		</li>
	</ul>
	<h2>Styling for forced colors</h2>
	<p>
		Normally, you don't need to do anything specific to support forced colors. But there are some
		gotchas you need to pay attention to
	</p>
	<p>
		If needed, you can used the <a
			href="https://developer.mozilla.org/en-US/docs/Web/CSS/@media/forced-colors">forced-colors</a>
		media query to style for forced colors mode.
	</p>

	<h2>Forced colors gotchas</h2>
	<ul class="flex flex-col gap-4">
		<li class="item-with-shadow">
			Shadows are gone. So if you use a shadow as differentiator you need to replace it.
		</li>
		<li class="item-with-background">
			All background colors are converged into one. If you use different background colors to
			separate elements, you need to use an outline instead.
		</li>
		<li>
			<p>
				If colours are used to convey meaning (which is a bad idea anyways, see <a
					href="https://www.w3.org/WAI/WCAG22/quickref/#use-of-color">WCAG 1.4.1</a
				>), this will no longer work. Add another indicator.
			</p>
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
		<li>
			Only native semantics are supported. Aria-attributes are not taken into account.
			<br />
			One example: buttons that are disabled using only aria-disabled are not shown as disabled in forced-colors
			mode.
			<div class="flex gap-2">
				<button class="wannabe-button" onclick={() => alert('Active Button Clicked')}
					>Active button</button>
				<button disabled class="wannabe-button">Disabled button</button>
				<button class="wannabe-button" aria-disabled="true">Aria-disabled button</button>
			</div>
		</li>
	</ul>

	<div class="styled-with-system-colors flex flex-col items-start gap-4 py-4">
		<h2 class="text-xl">Example: Focus outlines</h2>
		<p>
			Focus outlines should be visible regardless of light or dark mode with and without forced
			colors active. This can be done with an universal focus indicator. Tab to the button to test.
		</p>
		<button class="proper-focus w-20 border border-gray-500">A button</button>
		<samp>{@html buttonFocusStyle}</samp>
		<p>
			More on focus styles in the
			<a href="https://www.sarasoueidan.com/blog/focus-indicators">
				guide to designing accessible focus styles</a
			>.
		</p>
	</div>
</div>

<style>
	.item-with-shadow {
		padding: 0.5rem;
		box-shadow:
			-2px -2px 5px green,
			2px 2px 5px green;
	}

	.item-with-background {
		padding: 0.5rem;
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

	.wannabe-button {
		background-image: linear-gradient(#f7f8fa, #e7e9ec);
		border-color: #adb1b8 #a2a6ac #8d9096;
		border-style: solid;
		border-width: 1px;
		border-radius: 3px;
		box-shadow: rgba(255, 255, 255, 0.6) 0 1px 0 inset;
		box-sizing: border-box;
		color: #0f1111;
		cursor: pointer;
		display: inline-flex;
		justify-content: center;
		align-items: center;
		outline: 0;
		padding: 0.8rem;
	}

	.wannabe-button:disabled {
		color: #a2a6ac;
	}

	[aria-disabled='true'] {
		color: #a2a6ac;
	}

	.wannabe-button:hover {
		border-color: #a2a6ac #979aa1 #82858a;
	}

	.wannabe-button:focus-visible {
		outline: 2px solid ButtonBorder;
		outline-offset: 2px;
	}

	.proper-focus:focus-visible {
		outline: 3px solid black;
		box-shadow: 0 0 0 6px white;
	}

	@media (forced-colors: active) {
		.proper-focus:focus-visible {
			outline: 3px solid CanvasText;
		}
	}

	.proper-focus:hover {
		color-scheme: light dark;
		color: light-dark(var(--color-theme-2), var(--color-theme-4));
		border-color: light-dark(var(--color-theme-2), var(--color-theme-4));
	}
</style>
