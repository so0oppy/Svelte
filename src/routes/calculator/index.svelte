<script lang="ts">
    import { Button } from '@src/components/button';

    const textNumbers : string[] = [' ', ' ', ' ','7', '8', '9', '4', '5', '6', '1', '2', '3', '+/-', '0', '.']; 
    const textOperators: string[] = ['÷','×', '-', '+', '='];
    const textETC: string[] = ['%', 'CE', 'C', 'back'];

    function plus(a:number, b:number){
        return a + b;
    }
    function minus(a:number, b:number){
        return a - b;
    }
    function multiply(a:number, b:number){
        return a * b;
    }
    function div(a:number, b:number){
        return a / b;
    }
</script>

    <div class="display-area">
        0  
    </div>

    <div class="frame_etc">
        {#each textETC as text}
        <Button {text} color="dark-grey" onClick={(value) => alert(value)} />
            {/each}
    </div>

    <div class="frame">

        <div class ="frame_num">
            {#each textNumbers as text}
                <Button {text} color="orange" onClick={(value) => alert(value)} />
                    {/each}
        </div>
        <div class="frame_oper">
            {#each textOperators as text}
            <Button {text} color="grey" onClick={(value) => alert(value)} />
                {/each}
        </div>

    </div>
    

<style lang="scss">
    .display-area{
        font-size: 40px;
        font-weight: 600;
        text-align: left;
        width: 320px;
        height: 80px;
        display: flex;
        flex-wrap: wrap;
        background-color: darkgray;
    }
    .frame{
        display: flex;
    }
    .frame_etc{
        width: 320px;
        display: flex;
        flex-wrap: wrap;
    }
    .frame_num {
        width: 240px;
        display: flex;
        flex-wrap: wrap;
    }
    .frame_oper{
        width: 80px;
        display: flex;
        flex-wrap: wrap;
    }
</style>