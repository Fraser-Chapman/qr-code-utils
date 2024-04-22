<script lang="ts">
	import QRCode from 'qrcode';
	let inputValue: string;

	function generateCode(input: string): void {
		QRCode.toDataURL(input, function (err, url) {
			console.log(url);
		})
	}

</script>

<div class="container h-full mx-auto flex justify-center items-center">
	<div class="space-y-10 text-center flex flex-col items-center">
		<h2 class="h2">Generate QR</h2>

		<div id="container">
			<input class="input" type="text" name="input" id="input" placeholder="url" bind:value={inputValue} on:change="{generateCode(inputValue)}">
		</div>
	</div>
</div>
