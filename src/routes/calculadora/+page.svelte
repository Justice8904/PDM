<script>
	import { clear } from "console";

    let num1 = $state()
    let num2 = $state()
    let res = $state()
    let currentOperation = $state("")

    function eq(){
        
    }
</script>
<div class="text-center">
    <input class="form-control-lg w-100 mt-3" type="number" readonly />
    <table class="table table-borderless table-sm">
        <tbody>
            <tr>
                <td><button type="button" class="btn btn-outline-danger w-100" onclick={() => clear()}>C</button></td>
                <td><button type="button" class="btn btn-outline-warning w-100" onclick={() => press("(")}>&lpar;</button></td>
                <td><button type="button" class="btn btn-outline-warning w-100" onclick={() => press(")")}>&rpar;</button></td>
                <td><button type="button" class="btn btn-outline-warning w-100" onclick={() => press("/")}>/</button></td>
            </tr>
            <tr>
                <td><button type="button" class="btn btn-outline-dark w-100" onclick={() => press(7)}>7</button></td>
                <td><button type="button" class="btn btn-outline-dark w-100" onclick={() => press(8)}>8</button></td>
                <td><button type="button" class="btn btn-outline-dark w-100" onclick={() => press(9)}>9</button></td>
                <td><button type="button" class="btn btn-outline-warning w-100" onclick={() => press("*")}>X</button></td>
            </tr>
            <tr>
                <td><button type="button" class="btn btn-outline-dark w-100" onclick={() => press(4)}>4</button></td>
                <td><button type="button" class="btn btn-outline-dark w-100" onclick={() => press(5)}>5</button></td>
                <td><button type="button" class="btn btn-outline-dark w-100" onclick={() => press(6)}>6</button></td>
                <td><button type="button" class="btn btn-outline-warning w-100" onclick={() => press("-")}>&minus;</button></td>
            </tr>
            <tr>
                <td><button type="button" class="btn btn-outline-dark w-100" onclick={() => press(1)}>1</button></td>
                <td><button type="button" class="btn btn-outline-dark w-100" onclick={() => press(2)}>2</button></td>
                <td><button type="button" class="btn btn-outline-dark w-100" onclick={() => press(3)}>3</button></td>
                <td rowspan="2" style="height: 0;"><button type="button" class="btn btn-outline-warning w-100 h-100" onclick={() => press("+")}>&plus;</button></td>
            </tr>
            <tr>
                <td><button type="button" class="btn btn-outline-dark w-100" onclick={() => press(0)}>0</button></td>
                <td><button type="button" class="btn btn-outline-warning w-100" onclick={() => press(".")}>&sdot;</button></td>
                <td><button type="button" class="btn btn-outline-warning w-100" onclick={() => eq()}>&equals;</button></td>
                <td></td>
            </tr>
        </tbody>
    </table>
</div>