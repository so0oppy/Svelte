<script lang="ts">
    import { Button } from '@src/components/button';
    import { Display } from '@src/components/display';
    //Button
    const textNumbers : string[] = ['7', '8', '9', '4', '5', '6', '1', '2', '3', '0']; //소숫점 나중에 추가 
    const textOperators: string[] = ['÷', '×', '-', '+', '='];
    const textETC: string[] = ['AC', '+/-', '%'];

    //변수
    let Result: number = 0;

    let num1: number = 0;
    let num2: number = 0;
    let operator: string; // 연산부호

    //사칙연산 함수
    function plus(x:number): void{
        num1 = x;
        operator = '+';
        Result = 0;
    }
    function minus(x:number): void{
        num1 = x;
        operator = '-';
        Result = 0;
    }
    function multiply(x:number): void{
        num1 = x;
        operator = '×';
        Result = 0;
    }
    function div(x:number): void{
        num1 = x;
        operator = '÷';
        Result = 0;
    }
    //이외 연산 함수
    function clear(): void{  // All Clear
        operator = ' ';
        Result = 0;
    }
    function pos_neg(): void{  // +/-
        Result *= -1;
    }
    function percent(x:number): void{
        num1 = x;
        operator = '%';
        Result = num1 / 100;
    }
    // function equal(){
    //     operator = '=';
    //     calculator();
    //     return Result;
    // }
    //사칙연산 계산하는 함수
    function calculator(): void{
        num2 = Result;
        switch(operator){
            case '+':
                Result = num1 + num2;
                break;
            case '-':
                Result = num1 - num2;
                break;
            case '×':
                Result = num1 * num2;
                break;
            case '÷':
                Result = num1 / num2;
                break;
            default:
                break;
        }
    }

    //두자리 이상 입력 시, 자리수가 바뀌도록 하는 함수
    function update(val:number): void{
        Result = Result*10 + val;
    }

</script>

    <div class="display-area">
        <Display color="grey" result={Result}></Display>
    </div>
    
    <div class="frame">
        <div>
            <div class="frame_etc">
                <Button text={textETC[0]} color="dark-grey" onClick={(value) => clear()}/>
                <Button text={textETC[1]} color="dark-grey" onClick={(value) => pos_neg()}/>
                <Button text={textETC[2]} color="dark-grey" onClick={(value) => percent(Result)}/>
            </div>
    
            <div class ="frame_num">
                {#each textNumbers as text}
                    <Button {text} color="grey" onClick={(value) => update(parseInt(value))} />
                        {/each}
            </div>
        </div>

        <div class="frame_oper">
            <Button text={textOperators[0]} color="orange" onClick={(value) => div(Result)} />
            <Button text={textOperators[1]} color="orange" onClick={(value) => multiply(Result)} />
            <Button text={textOperators[2]} color="orange" onClick={(value) => minus(Result)} />
            <Button text={textOperators[3]} color="orange" onClick={(value) => plus(Result)} />
            <Button text={textOperators[4]} color="orange" onClick={(value) => calculator()} />
        </div>
    </div>
        

<style lang="scss">
    .display-area{
        width: 320px;
        height: 100px;
        display: flex;
        flex-wrap: wrap;
    }
    .frame{
        display: flex;
        width: 320px;
        height: 400px;
    }
    .frame_etc{
        width: 240px;
        height: 80px;
        display: flex;
        flex-wrap: wrap;
    }
    .frame_num {
        width: 240px;
        height: 320px;
        display: flex;
        flex-wrap: wrap;
        background-color: grey;
    }
    .frame_oper{
        width: 80px;
        height: 320px;
        display: flex;
        flex-wrap: wrap;
    }
</style>