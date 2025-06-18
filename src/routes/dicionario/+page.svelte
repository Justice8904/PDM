<script>
    import { palavras } from "$lib/palavras";
    let termoPesquisado = $state('');
    let termosFiltrados = $state([])
    let luckyNumber = $state(palavras.keys().toArray())
    let random = $state()
    let palavra = $state('')

    function filtro() {
      if (termoPesquisado == '') {
        termosFiltrados = palavras.keys().toArray()
        return
      }
      termosFiltrados = palavras.keys().filter(palavra => palavra.toLowerCase().startsWith(termoPesquisado.toLowerCase())).toArray();
    }

    function randomWord() {
      random = luckyNumber[Math.trunc(Math.random()*luckyNumber.length)]
    }
    filtro()
    randomWord()
</script>

<style>
  main {
    font-family: sans-serif;
    max-width: 800px;
    margin: 20px auto;
    padding: 20px;
    border: 1px solid #eee;
    border-radius: 8px;
    box-shadow: 0 2px 4px rgba(0,0,0,0.1);
  }
  h1 {
    text-align: center;
    color: #333;
  }
  input {
    width: calc(100% - 20px);
    padding: 10px;
    margin-bottom: 20px;
    border: 1px solid #ddd;
    border-radius: 4px;
    font-size: 16px;
  }
  .termo {
    margin-bottom: 15px;
    padding: 10px;
    border: 1px solid #e0e0e0;
    border-radius: 6px;
    background-color: #f9f9f9;
    text-align: center;
  }
  .no-results {
    text-align: center;
    color: #777;
    padding: 20px;
  }
  .palavra {
    font-size: x-large;
    text-decoration: none;

  }
  .btn {
    margin-bottom: 5%;
  }
</style>

<main>
  <h1>Dicionário Rodolfo</h1>
<center>
  <input
    type="text"
    bind:value={termoPesquisado}
    oninput={filtro}
    placeholder="Pesquise por um termo..."
  />

  <a href="/dicionario/{random}" type="button" class="btn btn-outline-info" onclick={randomWord}>Me sinto com sorte</a></center>

  {#if termosFiltrados.length > 0}
    {#each termosFiltrados as palavra}
      <div class="termo">
        <a href="/dicionario/{palavra}" class="palavra">{palavra}</a>
      </div>
    {/each}
  {:else}
    <p class="no-results">Nenhum termo encontrado para "{termoPesquisado}".</p>
  {/if}
</main>
