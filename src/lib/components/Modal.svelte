<script>
  let { msg, acao } = $props();
</script>

<div class="modal fade" id="alertaModal" tabindex="-1">
  <div class="modal-dialog modal-dialog-centered">
    <div class="modal-content">
      <center><div class="modal-body fs-3 fw-bold">{msg}</div></center>
        <div class="modal-footer">
            <button class="btn btn-success btn-gradient" data-bs-dismiss="modal" onclick={acao}>Fodase</button>
        </div>
    </div>
  </div>
</div> 