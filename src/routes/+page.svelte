<script lang="ts">
	import QRCode from 'qrcode';

	let inputValue: string;

	function generateCode(input: string): void {
			const canvas = document.getElementById('canvas')

			QRCode.toCanvas(canvas, input, function(error) {
				if (error) {
					console.log(error)
				}
			})

	}

</script>

<div class="container h-full mx-auto flex justify-center items-center">
	<div class="space-y-10 text-center flex flex-col items-center">
		<h2 class="h2">Generate QR</h2>

		<div id="container" class="flex flex-col max-w-96">
			<input class="input" type="text" name="input" id="input" placeholder="url" bind:value={inputValue} on:change="{generateCode(inputValue)}">
			<canvas id="canvas"></canvas>
		</div>
	</div>
</div>
