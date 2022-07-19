<script lang="ts">
    export let result : number; //함수타입
    export let color : 'grey';
</script>

<div class="display" data-color={color}>{result}</div>

<style lang="scss">
    .display {
        width: 320px;
        height: 100px;
        display : flex;
        align-items: center;
        justify-content: right;
        padding-right: 15px;
        font-size: 40px;
        font-weight: 600;

        &[data-color='grey'] {
            background-color: grey;
        }
    }
</style>