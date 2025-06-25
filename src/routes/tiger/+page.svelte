<script>
    import { games } from "$lib/games.js"
</script>

<center><h1>Misfortune Frog</h1></center>
<div class="container-fluid">
    <div class="row justify-content-md-center">
        {#each games as game}
        <div class="card" style="width: 18rem;">
            <img src={game.img} class="card-img-top" alt="...">
            <div class="card-body">
                <h5 class="card-title" style="text-transform: capitalize;">{game.name}</h5>
                <p class="card-text">{game.descricao}</p>
                <a href="tiger/{game.link}" class="btn btn-primary">Jogar</a>
            </div>
        </div>
        {/each}
    </div>
</div>

<style>
    .card{
        margin: 0.5%;
    }
    h1{
      text-decoration: underline;  
    }
</style>