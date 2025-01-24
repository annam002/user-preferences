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
&nbsp;&nbsp;color-scheme: light;<br>
&nbsp;&nbsp;background: #cedce8;<br>
&nbsp;&nbsp;color: #3d4245;<br>
&nbsp;&nbsp;padding: 1rem 1rem;<br>
  <br>
.style-for-dark-scheme {<br>
&nbsp;&nbsp;color-scheme: dark;<br>
&nbsp;&nbsp;background: #3d4245;<br>
&nbsp;&nbsp;color: #cedce8;<br>
&nbsp;&nbsp;padding: 1rem 1rem;<br>
}`;
</script>

<svelte:head>
	<title>Color Scheme</title>
</svelte:head>

<div class="text-column">
	<p>Toggle light and dark mode in OS to see the changes on this page.</p>

	<div class="flex flex-col items-start gap-4 py-4">
		<h2>Using color-scheme prop</h2>
		<div class="style-for-light-scheme">This is a box which only supports light scheme</div>
		<div class="style-for-dark-scheme">This is a box which only supports dark scheme</div>
		<samp>{@html colorScheme}</samp>
		<p>
			Link to documentation:
			<a href="https://developer.mozilla.org/en-US/docs/Web/CSS/color-scheme">color-scheme</a>
		</p>
	</div>
	<div class="mb-8 flex flex-col items-start gap-8 py-4">
		<h2>Demonstrating differences with color-scheme</h2>
		<div class="grid grid-cols-2 gap-12">
			<div class="flex h-[200px] flex-col gap-4 overflow-y-scroll px-4" style="color-scheme:none">
				<h3>Without color-scheme set</h3>
				<label>Name: <input type="text" /></label>
				<label>I agree: <input type="radio" /></label>
				<p>Lorem ipsum dolor si amet.</p>
				<p>Lorem ipsum dolor si amet.</p>
				<p>Lorem ipsum dolor si amet.</p>
			</div>
			<div class="flex h-[200px] flex-col gap-4 overflow-y-scroll px-4">
				<h3>With color-scheme: light dark</h3>
				<label>Name: <input type="text" /></label>
				<label>I agree: <input type="radio" /></label>
				<p>Lorem ipsum dolor si amet.</p>
				<p>Lorem ipsum dolor si amet.</p>
				<p>Lorem ipsum dolor si amet.</p>
			</div>
		</div>
	</div>
</div>

<style>
	.style-for-light-scheme {
		color-scheme: light;
		background: #cedce8;
		color: #3d4245;
		padding: 2rem;
	}
	.style-for-dark-scheme {
		color-scheme: dark;
		background: #3d4245;
		color: #cedce8;
		padding: 2rem;
	}
</style>
