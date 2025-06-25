<script>
	import { numbers } from '$lib/numbers';
	import Modal from '$lib/components/Modal.svelte';
    import ModalPix from '$lib/components/ModalPix.svelte';
	import * as bootstrap from 'bootstrap';
	import { onMount } from 'svelte';
	let randomNumber = $state(numbers.keys().toArray());
	let random = $state();
	let slots = $state([]);
	let saldo = $state(10);
	let custom = $state(0);
	let msg = $state('');
    let img = $state()
	let codigo = $state('');
	let m = $state();
    let p = $state();
	function casino() {
		if (saldo >= 10) {
			slots = [];
			for (let i = 0; i < 3; i++) {
				slots.push(Math.trunc(Math.random() * randomNumber.length));
			}
			saldo -= 10;
			msg = '';
		} else {
			msg = 'Saldo Insuficiente!';
			m.show();
		}
		if ((slots[0] == 7 && slots[1] == 7 && slots[2] == 7) || codigo == 'eotigras') {
			msg = 'Grande Prêmio!!!, entre em www.clonacartão.com.br para resgatar seu prêmio.';
			saldo *= 10;
			m.show();
		} else if ((slots[0] == 6 && slots[1] == 9 && slots[2] == 9) || codigo == 'atlas') {
			msg = 'Okarun? Uwu';
			saldo *= 6.99;
			m.show();
		} else if ((slots[0] == 0 && slots[1] == 0 && slots[2] == 0) || codigo == 'otario') {
			msg = 'Faz o L! kkkkkkkkkkkkkkkkkkk';
			saldo *= 0;
			m.show();
		} else if ((slots[0] == slots[1] && slots[0] == slots[2]) || codigo == 'sora') {
			msg = 'Parabéns pela vitória!';
			saldo *= slots[0];
			m.show();
		}
        codigo = '';
	}
	function addSaldo(s) {
        p.show()
		saldo += s;

	}
	onMount(() => {
		m = new bootstrap.Modal('#alertaModal');
        p = new bootstrap.Modal('#alertaPix');
	});
	casino();
</script>

<div class="container">
	<center
		><p
			class="fs-1 fw-bold text-decoration-underline"
			style="font-family:'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;"
		>
			Misfortune Frog
		</p></center
	>
	<div class="row justify-content-md-center">
		<div class="col slot">
			<img src={numbers.get(slots[0])} alt="" class="img-fluid" />
		</div>
		<div class="col slot">
			<img src={numbers.get(slots[1])} alt="" class="img-fluid" />
		</div>
		<div class="col slot">
			<img src={numbers.get(slots[2])} alt="" class="img-fluid" />
		</div>
	</div>
	<br />
</div>
<div class="d-grid gap-2 col-6 mx-auto">
	<button class="btn btn-warning fs-3" onclick={casino}>Rolada</button>
</div>
<br />
<Modal {msg} />
<ModalPix {img} />
<br />
<input class="form-control form-control-lg" placeholder="Saldo" type="number" bind:value={saldo} readonly/>
<br />
<center>
	<h3>Adicionar Saldo</h3>
	<div class="d-grid gap-2 mx-auto">
		<div class="btn-group-lg">
			<button type="button" class="btn btn-success" onclick={() => addSaldo(10)}>10</button>
			<button type="button" class="btn btn-success" onclick={() => addSaldo(100)}>100</button>
			<button type="button" class="btn btn-success" onclick={() => addSaldo(1000)}>1000</button>
			<button type="button" class="btn btn-success" onclick={() => addSaldo(custom)}>Custom</button>
		</div>
		<div>
			<input
				class="form-control form-control-lg"
				placeholder="Saldo"
				type="number"
				bind:value={custom}
			/>
		</div>
	</div>
</center>
<br />
<input class="form-control form-control-lg" placeholder="Código" type="text" bind:value={codigo} />
<br />

<center><a href="/tiger" type="button" class="btn btn-outline-info btn-lg">Retornar ao menu</a></center>


<style>
	.slot {
		background-color: blanchedalmond;
		border: black, solid, 3px;
	}
</style>
