<script lang="ts">
    import Tag from "$component/compartilhados/Tag.svelte";
    import {minhaLista} from "../../../stores/minhaLista";

    export let ingrediente: string;

    //sintaxe de código reativo
    $: selecionado = $minhaLista.includes(ingrediente);

    function aoClicar() {
        if (!selecionado) {
            minhaLista.adicionarIngrediente(ingrediente);
        } else {
            minhaLista.removerIngrediente(ingrediente);
        }
    }
</script>

<button on:click={aoClicar}>
    <Tag ativa={selecionado}>{ingrediente}</Tag>
</button>

<style>
    button {
        cursor: pointer;
    }
</style>
