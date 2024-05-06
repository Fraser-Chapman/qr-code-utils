<script lang="ts">
	import QRCode from 'qrcode';

	let inputValue: string;

	function generateCode(input: string): void {
		const canvas: HTMLCanvasElement = document.getElementById('qr') as HTMLCanvasElement

		QRCode.toCanvas(canvas, input, function(error) {
			if (error) {
				console.log(error)
			}
		})

		const downloadLink: HTMLAnchorElement = document.createElement('a');
		downloadLink.setAttribute('download', 'qr.png');
		downloadLink.setAttribute('href', canvas.toDataURL("image/png").replace("image/png", "image/octet-stream"));
		downloadLink.click()
	}

</script>

<main class="container h-full mx-auto flex justify-center items-center">
	<section class="space-y-10 text-center flex flex-col items-center">
		<h2 class="h2">Generate QR</h2>

		<section id="container" class="flex flex-col items-center content-between gap-7">
			<input class="input" type="text" name="input" id="input" placeholder="url" bind:value={inputValue} on:change="{generateCode(inputValue)}">
			<canvas id="qr" width="100%" height="100%"></canvas>
			<link id="downloadLink">
		</section>
	</section>
</main>
