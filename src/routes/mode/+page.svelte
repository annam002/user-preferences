<script>
	const example1 = `.example1 {<br>
&nbsp;&nbsp;color-scheme: light dark;<br>
&nbsp;&nbsp;color: CanvasText;<br>
&nbsp;&nbsp;background-color: Canvas;<br>
}`;
	const example2 = `.example2 {<br>
&nbsp;&nbsp;color-scheme: light dark;<br>
&nbsp;&nbsp;color: light-dark(#731, #dcb);<br>
&nbsp;&nbsp;background-color: light-dark(#dca, #753);<br>
}`;

	const example3 = `.example3 {<br>
&nbsp;&nbsp;background: #dca;<br>
&nbsp;&nbsp;color: #731;<br>
}<br>
@media (prefers-color-scheme: dark) {<br>
&nbsp;&nbsp;.example3 {<br>
&nbsp;&nbsp;&nbsp;background: #753;<br>
&nbsp;&nbsp;&nbsp;color: #dcb;<br>
&nbsp;&nbsp;&nbsp;outline: 5px dashed #000;<br>
&nbsp;&nbsp;}<br>
}`;

	const example4 = `button:focus-visible {<br>
&nbsp;&nbsp;outline: 3px solid black;<br>
&nbsp;&nbsp;box-shadow: 0 0 0 6px white;<br>
}`;
</script>

<svelte:head>
	<title>Light & Dark Mode</title>
</svelte:head>

<div class="text-column">
	<h1>Light & Dark Mode</h1>

	<p>Toggle light and dark mode in OS to see the changes on this page.</p>

	<div class="example1 flex w-[750px] flex-col gap-4 p-4">
		<h2>Using the color-scheme CSS property</h2>
		<samp>{@html example1}</samp>
		<p>
			Link to documentation:
			<a href="https://developer.mozilla.org/en-US/docs/Web/CSS/color-scheme">color-scheme</a>
		</p>
	</div>

	<div class="example2 flex w-[750px] flex-col gap-4 p-4">
		<h2>Using light-dark CSS property</h2>
		<samp>{@html example2}</samp>
		<p>
			Not (yet) supported in all browsers, check
			<a href="https://caniuse.com/?search=light-dark">can-i-use page</a>.
		</p>
		<p>
			Link to documentation:
			<a href="https://developer.mozilla.org/en-US/docs/Web/CSS/color_value/light-dark">
				light-dark</a
			>.
		</p>
	</div>

	<div class="example3 flex w-[750px] flex-col gap-4 p-4">
		<h2>Using prefers-color-scheme media query</h2>
		<samp>{@html example3}</samp>
		<p>
			Link to documentation:
			<a href="https://developer.mozilla.org/en-US/docs/Web/CSS/@media/prefers-color-scheme">
				prefers-color-scheme</a>
		</p>
	</div>

	<div class="example1 flex w-[750px] flex-col gap-4 p-4">
		<h2 class="text-xl">Focus outlines</h2>
		<p>
			Focus outlines should be visible regardless of light or dark mode. This can be done with an
			universal focus indicator. Tab to the button to test.
		</p>
		<button class="w-20 border border-gray-500">A button</button>
		<samp>{@html example4}</samp>
		<p>
			More on focus styles in the
			<a href="https://www.sarasoueidan.com/blog/focus-indicators">
				guide to designing accessible focus styles</a
			>.
		</p>
	</div>
</div>

<style>
	.example1 {
		color-scheme: light dark;
		color: CanvasText;
		background-color: Canvas;
	}

	.example2 {
		color-scheme: light dark;
		color: light-dark(#731, #dcb);
		background-color: light-dark(#dca, #753);
	}

	.example3 {
		background: #dca;
		color: #731;
	}
	@media (prefers-color-scheme: dark) {
		.example3 {
			background: #753;
			color: #dcb;
		}
	}

	button:focus-visible {
		outline: 3px solid black;
		box-shadow: 0 0 0 6px white;
	}

	a {
		color-scheme: light dark;
		color: CanvasText;
		text-decoration: underline;
	}

	a:hover {
		color-scheme: light dark;
		color: light-dark(var(--color-theme-3), var(--color-theme-4));
	}

	button:hover {
		color-scheme: light dark;
		color: light-dark(var(--color-theme-2), var(--color-theme-4));
		border-color: light-dark(var(--color-theme-2), var(--color-theme-4));
	}
</style>
