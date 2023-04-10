<script lang="ts">
    import Tag from "$component/compartilhados/Tag.svelte";
    import {minhaLista} from "../../../stores/minhaLista";
    import {fade} from "svelte/transition";

    export let ingrediente: string;

    function removerIngrediente(): void {
        minhaLista.removerIngrediente(ingrediente);
    }
</script>

<div class="meu-ingrediente-container" transition:fade={{ duration: 200 }}>
    <Tag ativa={true}>{ingrediente}
        <button class="close" on:click={removerIngrediente}></button>
    </Tag>
    <span>
        <button class="remover" on:click={removerIngrediente}>Remover</button>
    </span>
</div>

<style>
    .meu-ingrediente-container {
        position: relative;
    }

    .close {
        background-image: url("icones/close.svg");
        height: 10px;
        width: 10px;
        cursor: pointer;

        position: absolute;
        top: 4px;
        right: 4px;
    }

    .remover {
        line-height: 24px;
        font-size: 0.875rem;
        color: var(--laranja);
        cursor: pointer;
    }
</style>