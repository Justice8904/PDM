<script>
  let { img, acao } = $props();
  
</script>

<div class="modal fade" id="alertaPix" tabindex="-1">
  <div class="modal-dialog modal-dialog-centered">
    <div class="modal-content">
        <center>
            <div class="modal-body fs-3 fw-bold"><img src="https://cdn.imgchest.com/files/4gdcxnrbkj4.png" style="width: 70%;"></div>
            <p class="fs-3 fw-bold">Adicione o seu saldo!</p>
        </center>
        <div class="modal-footer">
            <button class="btn btn-success btn-gradient" data-bs-dismiss="modal" onclick={acao}>Tá pago</button>
        </div>
    </div>
  </div>
</div> 


