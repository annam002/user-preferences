<script>
	const mediaQuery = `.styled-with-media-query {<br>
&nbsp;&nbsp;background: #dca;<br>
&nbsp;&nbsp;color: #731;<br>
}<br>
@media (prefers-color-scheme: dark) {<br>
&nbsp;&nbsp;.styled-with-media-query {<br>
&nbsp;&nbsp;&nbsp;background: #753;<br>
&nbsp;&nbsp;&nbsp;color: #dcb;<br>
&nbsp;&nbsp;}<br>
}`;

	const colorScheme = `.style-for-light-scheme {<br>
  color-scheme: light;<br>
  background: #cedce8;<br>
  color: #3d4245;<br>
  padding: 1rem 1rem;<br>
  br>
  style-for-dark-scheme {<br>
  color-scheme: dark;<br>
  background: #3d4245;<br>
  color: #cedce8;<br>
  padding: 1rem 1rem;<br>
}`;

	const styledWithSystemColors = `.styled-with-system-colors {<br>
  color-scheme: light dark;<br>
  color: CanvasText;<br>
  background-color: Canvas;<br>
}`;

	const styledWithLightDark = `.styled-with-light-dark {<br>
  color-scheme: light dark;<br>
  color: light-dark(#731, #dcb);<br>
  background-color: light-dark(#dca, #753);<br>
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

	<div class="flex flex-col items-start gap-4 py-4">
		<h2>Checking mode with prefers-color-scheme media query</h2>
		<samp>{@html mediaQuery}</samp>
		<div class="styled-with-media-query">This box looks good in light & dark theme</div>
		<p>
			Link to documentation:
			<a href="https://developer.mozilla.org/en-US/docs/Web/CSS/@media/prefers-color-scheme">
				prefers-color-scheme</a>
		</p>
	</div>

	<div class="flex flex-col items-start gap-4 py-4">
		<h2>Using color-scheme prop</h2>
		<samp>{@html colorScheme}</samp>
		<div class="style-for-light-scheme">This is a box which only supports light scheme</div>
		<div class="style-for-dark-scheme">This is a box which only supports dark scheme</div>
		<p>
			Link to documentation:
			<a href="https://developer.mozilla.org/en-US/docs/Web/CSS/color-scheme">color-scheme</a>
		</p>
	</div>

	<div class="flex flex-col items-start gap-4 py-4">
		<h2>Using system colors for dark/light mode</h2>
		<samp>{@html styledWithSystemColors}</samp>
		<div class="styled-with-system-colors">This box looks good in light & dark theme</div>
		<p>
			Link to documentation:
			<a href="https://developer.mozilla.org/en-US/docs/Web/CSS/system-color">system-color</a>
		</p>
	</div>

	<div class="flex flex-col items-start gap-4 py-4">
		<h2>Using light-dark CSS property</h2>
		<samp>{@html styledWithLightDark}</samp>
		<p>
			Not (yet) supported in all browsers, check
			<a href="https://caniuse.com/?search=light-dark">can-i-use page</a>.
		</p>
		<div class="styled-with-light-dark">This box looks good in light & dark theme</div>
		<p>
			Link to documentation:
			<a href="https://developer.mozilla.org/en-US/docs/Web/CSS/color_value/light-dark">
				light-dark</a
			>.
		</p>
	</div>

	<div class="styled-with-system-colors flex flex-col items-start gap-4 py-4">
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
	.styled-with-media-query {
		background: #cedce8;
		color: #3d4245;
		padding: 1rem 1rem;
	}
	@media (prefers-color-scheme: dark) {
		.styled-with-media-query {
			background: #3d4245;
			color: #cedce8;
		}
	}

	.style-for-light-scheme {
		color-scheme: light;
		background: #cedce8;
		color: #3d4245;
		padding: 1rem 1rem;
	}
	.style-for-dark-scheme {
		color-scheme: dark;
		background: #3d4245;
		color: #cedce8;
		padding: 1rem 1rem;
	}
	.styled-with-system-colors {
		color-scheme: light dark;
		color: CanvasText;
		background-color: Canvas;
		border: 1px solid ButtonBorder;
		padding: 1rem 1rem;
	}

	.styled-with-light-dark {
		color-scheme: light dark;
		color: light-dark(#3d4245, #cedce8);
		background-color: light-dark(#cedce8, #3d4245);
		padding: 1rem 1rem;
	}

	button:focus-visible {
		outline: 3px solid black;
		box-shadow: 0 0 0 6px white;
	}

	button:hover {
		color-scheme: light dark;
		color: light-dark(var(--color-theme-2), var(--color-theme-4));
		border-color: light-dark(var(--color-theme-2), var(--color-theme-4));
	}
</style>
