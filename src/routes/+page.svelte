<script>
    let total = 0;
    let console = "";
    let state = null;
    function resolveState(){
        switch(state){
            case "add":
                total+= parseFloat(console);
                console = "0";
                break;
            case "substract":
                total-= parseFloat(console);
                console = "0";
                break;
            case "multiply":
                total*= parseFloat(console);
                console = "0";
                break;
            case "divide":
                total/= parseFloat(console);
                console = "0";
                break;
            default:
                total= parseFloat(console);
                console = "0";
        }
    }
    function setOperation(operation){
        resolveState();
        state = operation;
    }
    function setValue(value){
        if(console.toString() == "0" || state == "equal"){
            console = "";
        }
        if(state == "equal"){
            state = null;
        }
        if(value == "C"){
            total=0;
            state = null;
            console = "";
            return;
        }
        console = console + value;
    }
    function equal(){
        resolveState();
        console = total;
        state = "equal";
    }
</script>

<style>
    .titulo{
        font-family: 'Poppins', sans-serif;
        text-align: center;
        background: #4fdaae;
        padding: 0.1%;
        margin: 0%;
        border-bottom: 3px solid black;
    }
    .calculator {
        position: absolute;
        top: 60%;
        left: 50%;
        transform: translate(-50%,-50%);
        width: 50%;
        border: 1px solid #656565;
        box-shadow: 2px 2px 2px #eeeeee;
        padding: 10px;   
    }
        .calculator input{
            box-sizing: border-box;
            width: 100%;
            padding: 20px;
            margin: auto;
            outline: none;
            text-align: right;
            font-size: 45px;
            font-family: 'Rajdhani', sans-serif;
            border: 2px solid black;
        }
        .calculator .buttons{
            display: flex;
            flex-wrap: wrap;
        }
            .calculator .buttons .operations{
                display: flex;
                justify-content: space-between;
                width: 100%;
                margin-top: 2%;
            }
                .calculator .buttons .operations button{
                    width: 24%;
                    padding: 20px 0;
                    font-family: 'Rajdhani', sans-serif;
                    font-size: 25px;
                    font-weight: bolder;
                    background:#818181;
                }
                .calculator .buttons .operations button:hover{
                    background:#686868;
                }
            .calculator .buttons .numbers{
                width: 75%;
            }
                .calculator .buttons .numbers > div {
                    display: flex;
                    justify-content: space-between;
                    margin: 5px 0;
                    }
                    .calculator .buttons .numbers > div button {
                        width: 32%;
                        padding: 10px 0;
                        font-family: 'Rajdhani', sans-serif;
                        font-size: 25px;
                        font-weight: bolder;
                        background:#ccc;
                    }
                        .calculator .buttons .numbers > div button:hover{
                            background: #aaa;
                        }
        .calculator .equal{
            flex: 1;
        }
            .calculator .equal button{
                margin-left: 5%;
                margin-top: 5%;
                width: 95%;
                height: 95%;
                background: #00af78;
                color: #eeeeee;
                font-size: 25px;
                font-weight: bolder;
            }
            .calculator .equal button:hover{
                background: #008057;
            }
        .calculator button{
            outline: none;
        }
</style>
<div class="titulo">
    <h1>Horacio Hazahel Mendoza Ramos</h1>
    <p>Página Web con una calculadora sencilla utilizando Svelte</p>
</div>
<div class="calculator">
    <input type="text" bind:value={console} readonly="true">
    <div class="buttons">
        <div class="operations">
            <button on:click={()=>{setOperation('add');}}>
                +
            </button>

            <button on:click={()=>{setOperation('substract');}}>
                -
            </button>

            <button on:click={()=>{setOperation('multiply');}}>
                &times;
            </button>

            <button on:click={()=>{setOperation('divide');}}>
                &divide;
            </button>
        </div>
        <div class="numbers">
            <div>
                <button on:click={()=>{setValue(7);}}>
                    7
                </button>
                <button on:click={()=>{setValue(8);}}>
                    8
                </button>
                <button on:click={()=>{setValue(9);}}>
                    9
                </button>
            </div>
            <div>
                <button on:click={()=>{setValue(4);}}>
                    4
                </button>
                <button on:click={()=>{setValue(5);}}>
                    5
                </button>
                <button on:click={()=>{setValue(6);}}>
                    6
                </button>
            </div>
            <div>
                <button on:click={()=>{setValue(1);}}>
                    1
                </button>
                <button on:click={()=>{setValue(2);}}>
                    2
                </button>
                <button on:click={()=>{setValue(3);}}>
                    3
                </button>
            </div>
            <div>
                <button on:click={()=>{setValue(0);}}>
                    0
                </button>
                <button on:click={()=>{setValue('.');}}>
                    .
                </button>
                <button on:click={()=>{setValue('C');}}>
                    C
                </button>
            </div>
        </div>
        <div class="equal">
            <button on:click={equal}>
                =
            </button>
        </div>

    </div>

</div>