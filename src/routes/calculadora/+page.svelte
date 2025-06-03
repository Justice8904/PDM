<script>
    let num1 = $state()
    let num2 = $state()
    let res = $state()
    let currentOperation = $state()

    function plus() {
       res = num1+num2
    }
    function minus() {
        res = num1-num2
    }
    function times() {
        res = num1*num2
    }
    function divide() {
        res = num1/num2
    }
    
</script>
<div class="text-center">
    <input class="form-control mt-3" type="number">
    <table class="table table-borderless">
        <tbody>
            <tr>
                <td><button type="button" class="btn btn-outline-danger w-100">C</button></td>
                <td><button type="button" class="btn btn-outline-warning w-100">&lpar;</button></td>
                <td><button type="button" class="btn btn-outline-warning w-100">&rpar;</button></td>
                <td><button type="button" class="btn btn-outline-warning w-100">/</button></td>
            </tr>
            <tr>
                <td><button type="button" class="btn btn-outline-dark w-100">7</button></td>
                <td><button type="button" class="btn btn-outline-dark w-100">8</button></td>
                <td><button type="button" class="btn btn-outline-dark w-100">9</button></td>
                <td><button type="button" class="btn btn-outline-warning w-100">X</button></td>
            </tr>
            <tr>
                <td><button type="button" class="btn btn-outline-dark w-100">4</button></td>
                <td><button type="button" class="btn btn-outline-dark w-100">5</button></td>
                <td><button type="button" class="btn btn-outline-dark w-100">6</button></td>
                <td><button type="button" class="btn btn-outline-warning w-100">&minus;</button></td>
            </tr>
            <tr>
                <td><button type="button" class="btn btn-outline-dark w-100">1</button></td>
                <td><button type="button" class="btn btn-outline-dark w-100">2</button></td>
                <td><button type="button" class="btn btn-outline-dark w-100">3</button></td>
                <td rowspan="2" style="height: 0;"><button type="button" class="btn btn-outline-warning w-100 h-100">&plus;</button></td>
            </tr>
            <tr>
                <td><button type="button" class="btn btn-outline-dark w-100">0</button></td>
                <td><button type="button" class="btn btn-outline-warning w-100">&sdot;</button></td>
                <td><button type="button" class="btn btn-outline-warning w-100">&equals;</button></td>
                <td></td>
            </tr>
        </tbody>
    </table>
</div>