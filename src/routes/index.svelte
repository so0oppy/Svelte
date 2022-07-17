<script lang="ts">
    import {button} from '@src/components/button';
    
    const textNumbers: string[] =
        ['1', '2', '3', '4', '5', '6', '7', '8', '9', '0']; 
</script>

<div class="frame">
    {#each textNumbers as text}
        <button {text} color="orange" onclick={(value) => alert{value}}></button>
    {/each}
</div>

<style lang="scss">
    .frame{
        width:240px;
        display: flex;
        flex-wrap: wrap;
    }
</style>