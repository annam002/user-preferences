<script>
	const styledWithSystemColors = `.styled-with-system-colors {<br>
&nbsp;&nbsp;color-scheme: light dark;<br>
&nbsp;&nbsp;color: CanvasText;<br>
&nbsp;&nbsp;background-color: Canvas;<br>
}`;
</script>

<svelte:head>
	<title>System Colors</title>
</svelte:head>

<div class="text-column schemed">
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
</div>

<style>
	.styled-with-system-colors {
		color-scheme: light dark;
		color: CanvasText;
		background-color: Canvas;
		border: 1px solid ButtonBorder;
		padding: 2rem;
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
