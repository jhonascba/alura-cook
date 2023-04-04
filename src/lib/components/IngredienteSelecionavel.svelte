<script lang="ts">
    import Tag from "$component/Tag.svelte";
    import {minhaLista} from "../stores/minhaLista";

    export let ingrediente: string;

    let selecionado = false;

    function aoClicar() {
        selecionado = !selecionado;

        if (selecionado) {
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
