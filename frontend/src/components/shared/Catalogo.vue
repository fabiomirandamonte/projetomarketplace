<template>
    <section id="catalogo">
        <div class="categoria">
            <div></div>
            <span>Eletrônicos</span>
        </div>
        <div class="categoria">
            <div></div>
            <span>Roupas</span>
        </div>
        <div class="categoria">
            <div></div>
            <span>Alimentos</span>
        </div>
        <div class="categoria">
            <div></div>
            <span>Decoração</span>
        </div>
        <div class="categoria">
            <div></div>
            <span>Esportes</span>
        </div>
        <div class="categoria">
            <div></div>
            <span>Beleza</span>
        </div>
        <div class="categoria">
            <div></div>
            <span>Livros</span>
        </div>
    </section>
</template>

<style scoped>
section#catalogo {
    width: 776px;
    height: 139px;
    display: flex;
    gap: 18px;
    justify-content: center;
}

section#catalogo .categoria {
    width: 106px;
    height: 139px;
    margin-top: 10px;
}

section#catalogo .categoria span
{
    display: block;
    text-align: center;
    margin-top: 6px;
    font-size: 12px;
}

section#catalogo .categoria div{
    width: 106px;
    height: 106px;
    background: #DEEFFF;
    border-radius: 100px;
}

</style>