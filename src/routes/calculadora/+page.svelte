<script>
    let display = $state('')
    let backDisp = $state('')
    let c = $state('')

    

    function backSpace(){
        display = display.slice(0,-1)
        
    }

    function press(c){
        display+=c
    }

    function equals(){
        backDisp = display
        .replaceAll('^', '**')
        .replaceAll('÷', '/')
        .replaceAll('x', '*')

        if (display.includes("√")) {
            backDisp = backDisp.replaceAll("√", "Math.sqrt(")
            backDisp += ")"
        }
        if (display.includes("Rnd ")) {
            backDisp = backDisp.replaceAll("Rnd ", "Math.round(")
            backDisp += ")"
        }
        if (display.includes("log(")) {
            if (display.includes(")")) {
                backDisp = backDisp.replaceAll("log(", "Math.log10(")
            }
            else{
            backDisp = backDisp.replaceAll("log(", "Math.log10(")
            backDisp += ")"
            }
        }
        display = eval(backDisp)
        display = String(display)
        console.log(backDisp)
    }

    function clear(){
        display=""
    }
  function invert(){
        let expr = display.split('')
        for(let i = expr.length-1; i >= 0; i--){
            if(expr[i] == "-"){
                expr[i] = "+"
                display = expr.join('')
                return 
            } else if(expr[i] == "+"){
                expr[i] = "-"
                display = expr.join('')
                return
            } else if(expr[i] == "x" || expr[i] == "/" || expr[i] == "^" || expr[i] == "%" || expr[i] == "("){
                let expr1 = expr.slice(0, i+1)
                expr1 += "-"
                let expr2 = expr.slice(i+1, expr.length)
                expr1 = expr1.concat(expr2)
                display = expr1.replaceAll(",", "")
                return
            }
        }
        display = "-" + expr.join('')
    }

</script>
<div class="text-center">
    <input class="form-control-lg w-100 mt-3" readonly  bind:value={display}/>
    <table class="table table-borderless table-sm">
        <tbody>
            <tr>
                <td><button type="button" class="btn btn-outline-danger w-100" onclick={() => clear()}>C</button></td>
                <td><button type="button" class="btn btn-outline-secondary w-100" onclick={() => backSpace()}>Ce</button></td>
                <td><button type="button" class="btn btn-outline-warning w-100" onclick={() => press("(")}>&lpar;</button></td>
                <td><button type="button" class="btn btn-outline-warning w-100" onclick={() => press(")")}>&rpar;</button></td>
                <td><button type="button" class="btn btn-outline-warning w-100" onclick={() => press("÷")}>&div;</button></td>
                <td><button type="button" class="btn btn-outline-warning w-100" onclick={() => press("^")}>x<sup>y</sup></button></td>
            </tr>
            <tr>
                <td><button type="button" class="btn btn-outline-dark w-100" onclick={() => press(7)}>7</button></td>
                <td><button type="button" class="btn btn-outline-dark w-100" onclick={() => press(8)}>8</button></td>
                <td><button type="button" class="btn btn-outline-dark w-100" onclick={() => press(9)}>9</button></td>
                <td><button type="button" class="btn btn-outline-warning w-100" onclick={() => press("x")}>X</button></td>
                <td><button type="button" class="btn btn-outline-warning w-100" onclick={() => press("√")}>&radic;</button></td>
                <td><button type="button" class="btn btn-outline-warning w-100" onclick={() => press("**1/")}><sup>x</sup>&radic;</button></td>
            </tr>
            <tr>
                <td><button type="button" class="btn btn-outline-dark w-100" onclick={() => press(4)}>4</button></td>
                <td><button type="button" class="btn btn-outline-dark w-100" onclick={() => press(5)}>5</button></td>
                <td><button type="button" class="btn btn-outline-dark w-100" onclick={() => press(6)}>6</button></td>
                <td><button type="button" class="btn btn-outline-warning w-100" onclick={() => press("-")}>&minus;</button></td>
                <td><button type="button" class="btn btn-outline-warning w-100" onclick={() => press("Rnd ")}>Rnd</button></td>
                <td><button type="button" class="btn btn-outline-warning w-100" onclick={() => invert()}>+/-</button></td>
            </tr>
            <tr>
                <td><button type="button" class="btn btn-outline-dark w-100" onclick={() => press(1)}>1</button></td>
                <td><button type="button" class="btn btn-outline-dark w-100" onclick={() => press(2)}>2</button></td>
                <td><button type="button" class="btn btn-outline-dark w-100" onclick={() => press(3)}>3</button></td>
                <td rowspan="2" style="height: 0;"><button type="button" class="btn btn-outline-warning w-100 h-100" onclick={() => press("+")}>&plus;</button></td>
                <td><button type="button" class="btn btn-outline-warning w-100" onclick={() => press("log(")}>Log</button></td>
            </tr>
            <tr>
                <td><button type="button" class="btn btn-outline-dark w-100" onclick={() => press(0)}>0</button></td>
                <td><button type="button" class="btn btn-outline-warning w-100" onclick={() => press(".")}>&sdot;</button></td>
                <td><button type="button" class="btn btn-outline-warning w-100" onclick={() => equals()}>&equals;</button></td>
                <td><button type="button" class="btn btn-outline-warning w-100" onclick={() => press("%")}>&percnt;</button></td>
            </tr>
        </tbody>
    </table>
</div>