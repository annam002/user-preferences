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
</script>

<svelte:head>
	<title>Color Scheme</title>
</svelte:head>

<div class="text-column">
	<p>Toggle light and dark mode in OS to see the changes on this page.</p>

	<div class="flex flex-col items-start gap-4 py-4">
		<h2>Checking current scheme with prefers-color-scheme media query</h2>
		<div class="styled-with-media-query">This box looks good in light & dark theme</div>
		<samp>{@html mediaQuery}</samp>
		<p>
			Link to documentation:
			<a href="https://developer.mozilla.org/en-US/docs/Web/CSS/@media/prefers-color-scheme">
				prefers-color-scheme</a>
		</p>
	</div>
</div>

<style>
	.styled-with-media-query {
		background: #cedce8;
		color: #3d4245;
		padding: 2rem;
	}
	@media (prefers-color-scheme: dark) {
		.styled-with-media-query {
			background: #3d4245;
			color: #cedce8;
		}
	}
</style>
