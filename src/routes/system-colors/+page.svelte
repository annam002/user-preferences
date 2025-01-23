<script>
	const styledWithSystemColors = `.styled-with-system-colors {<br>
&nbsp;&nbsp;color-scheme: light dark;<br>
&nbsp;&nbsp;color: CanvasText;<br>
&nbsp;&nbsp;background-color: Canvas;<br>
}`;

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
	<title>System Colors</title>
</svelte:head>

<div class="text-column schemed">
	<h1>System Colors</h1>

	<p>Toggle light and dark mode in OS to see the changes on this page.</p>

	<p>
		Link to documentation:
		<a href="https://developer.mozilla.org/en-US/docs/Web/CSS/system-color">system-color</a>
	</p>

	<div class="flex flex-col items-start gap-4 py-4">
		<h2>Using system colors for dark/light mode</h2>
		<div class="styled-with-system-colors">This box looks good in light & dark theme</div>
		<samp>{@html styledWithSystemColors}</samp>

		<h2>Current system colors:</h2>
		<ul class="grid list-none grid-cols-2 gap-4">
			<li>
				<span class="color-box" style="background-color: AccentColor;"></span>
				<span>AccentColor</span>
			</li>
			<li>
				<span class="color-box" style="background-color: AccentColorText;"></span>
				<span>AccentColorText</span>
			</li>
			<li>
				<span class="color-box" style="background-color: ActiveText;"></span>
				<span>ActiveText</span>
			</li>
			<li>
				<span class="color-box" style="background-color: ButtonBorder;"></span>
				<span>ButtonBorder</span>
			</li>
			<li>
				<span class="color-box" style="background-color: ButtonFace;"></span>
				<span>ButtonFace</span>
			</li>
			<li>
				<span class="color-box" style="background-color: ButtonText;"> </span><span
					>ButtonText</span>
			</li>
			<li><span class="color-box" style="background-color: Canvas;"> </span><span>Canvas</span></li>
			<li>
				<span class="color-box" style="background-color: CanvasText;"> </span><span
					>CanvasText</span>
			</li>
			<li><span class="color-box" style="background-color: Field;"> </span><span>Field</span></li>
			<li>
				<span class="color-box" style="background-color: FieldText;"></span>
				<span>FieldText</span>
			</li>
			<li>
				<span class="color-box" style="background-color: GrayText;"></span>
				<span>GrayText</span>
			</li>
			<li>
				<span class="color-box" style="background-color: Highlight;"></span>
				<span>Highlight</span>
			</li>
			<li>
				<span class="color-box" style="background-color: HighlightText;"></span>
				<span>HighlightText</span>
			</li>
			<li>
				<span class="color-box" style="background-color: LinkText;"></span>
				<span>LinkText</span>
			</li>
			<li>
				<span class="color-box" style="background-color: Mark;"></span>
				<span>Mark</span>
			</li>
			<li>
				<span class="color-box" style="background-color: MarkText;"></span>
				<span>MarkText</span>
			</li>
			<li>
				<span class="color-box" style="background-color: SelectedItem;"></span>
				<span>SelectedItem</span>
			</li>
			<li>
				<span class="color-box" style="background-color: Canvas;"></span>
				<span>SelectedItemText</span>
			</li>
			<li>
				<span class="color-box" style="background-color: VisitedText;"></span>
				<span>VisitedText</span>
			</li>
		</ul>
	</div>

	<div class="styled-with-system-colors flex flex-col items-start gap-4 py-4">
		<h2 class="text-xl">Focus outlines</h2>
		<p>
			Focus outlines should be visible regardless of light or dark mode. This can be done with an
			universal focus indicator. Tab to the button to test.
		</p>
		<button class="w-20 border border-gray-500">A button</button>
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
	.styled-with-system-colors {
		color-scheme: light dark;
		color: CanvasText;
		background-color: Canvas;
		border: 1px solid ButtonBorder;
		padding: 2rem;
	}

	button:focus-visible {
		outline: 3px solid black;
		box-shadow: 0 0 0 6px white;
	}

	@media (forced-colors: active) {
		button:focus-visible {
			outline: 3px solid CanvasText;
		}
	}

	button:hover {
		color-scheme: light dark;
		color: light-dark(var(--color-theme-2), var(--color-theme-4));
		border-color: light-dark(var(--color-theme-2), var(--color-theme-4));
	}

	.color-box {
		width: 36px;
		height: 36px;
		display: inline-block;
		margin-left: 10px;
		border: 1px solid ButtonBorder;
	}
	li {
		display: flex;
		gap: 1rem;
		align-items: center;
	}
</style>
