<script>
    import { palavras } from "$lib/palavras";
    import { page } from "$app/state";
    
    let palavra = page.params.word
    let def = palavras.get(palavra)
</script>
<center>
    <div class="card border-light mb-3" style="max-width: 18rem;">
    <div class="card-body">
        <h5 class="card-title">{palavra}</h5>
        {#each def as d}
            <p class="card-text">{d}</p>
        {/each}
        <a href="/dicionario" class="btn btn-dark">Voltar</a>
    </div>
    </div>
</center>
<style>
   p {
    text-align: justify;
    font-size: large;
   }
    .card-title{
        text-align: center;
        font-size: x-large;
    }
</style>