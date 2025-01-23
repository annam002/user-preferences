<script>
	const styledWithLightDark = `.styled-with-light-dark {<br>
&nbsp;&nbsp;color-scheme: light dark;<br>
&nbsp;&nbsp;color: light-dark(#731, #dcb);<br>
&nbsp;&nbsp;background-color: light-dark(#dca, #753);<br>
}`;
</script>

<svelte:head>
	<title>light-dark</title>
</svelte:head>

<div class="text-column schemed">
	<h1>light-dark function</h1>

	<p>Toggle light and dark mode in OS to see the changes on this page.</p>

	<p>
		Link to documentation:
		<a href="https://developer.mozilla.org/en-US/docs/Web/CSS/color_value/light-dark">
			light-dark</a
		>.
	</p>
	<div class="flex flex-col items-start gap-4 py-4">
		<h2>Adapt styling to color scheme using light-dark CSS property</h2>
		<div class="styled-with-light-dark">This box looks good in light & dark theme</div>
		<samp>{@html styledWithLightDark}</samp>
		<p>
			Not (yet) supported in all browsers, check
			<a href="https://caniuse.com/?search=light-dark">can-i-use page</a>.
		</p>
	</div>
</div>

<style>
	.styled-with-light-dark {
		color-scheme: light dark;
		color: light-dark(#3d4245, #cedce8);
		background-color: light-dark(#cedce8, #3d4245);
		padding: 2rem;
	}
</style>
