<script lang="ts">
	import QRCode from 'qrcode';

	let inputValue: string;

	function generateCode(input: string): void {
		const canvas = document.getElementById('qr')
		QRCode.toCanvas(canvas, input, function(error) {
			if (error) {
				console.log(error)
			}
		})
	}

</script>

<main class="container h-full mx-auto flex justify-center items-center">
	<section class="space-y-10 text-center flex flex-col items-center">
		<h2 class="h2">Generate QR</h2>

		<section id="container" class="flex flex-col items-center content-between gap-7">
			<input class="input" type="text" name="input" id="input" placeholder="url" bind:value={inputValue} on:change="{generateCode(inputValue)}">
			<canvas id="qr" width="100%" height="100%"></canvas>
		</section>
	</section>
</main>
