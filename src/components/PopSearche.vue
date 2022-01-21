<template>
    <div id="modal-searche" class="modal-content">
        <div class="modal">
            <button class="close">x</button>
            <div>
                <h1>por Categoria</h1>
                <form>
                    <input type="text" class="input" placeholder="Categoria"/>
                </form>
            </div>
            <div id="table-content">
                <table class="table">
                    <tr v-for="dado in dados" :key="dado.id"><td>{{dado.category}}</td></tr>
                </table>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "PopSearch",
    data: () => ({

    }),
    props: {
        dados: null,
    }
}
</script>

<style scoped>
    .modal-content {
        width: 100vw;
        height: 100vh;
        background-color: rgba(0,0,0,.5);
        position: fixed;
        top: 0px;
        left: 0px;
        z-index: 2000;
        display: nome;
        justify-content: center;
        align-items: center;
    }
    .modal-content.mostar{
        display: flex;
    }
    .modal {
        position: relative;
        background: white;
        width: 60%;
        min-width: 300px;
        padding: 40px;
        border: 5px solid #424242;
        border-radius: 5px;
        box-shadow: 0 0 0 5px white;
    }
    #header {

    }
    .input{
        border: 3px solid #2e2d2d;
        border-radius: 3px;
    }
    .table{
        width: 100%;
        background-color:#01579B;
        align-items: center;
    }
    #table-content{
        width: 80vh;
    }
    .close{
        position: absolute;
        top: -15px;
        right: -15px;
        width: 40px;
        height: 40px;
        border-radius: 50%;
        border: 2px solid white;
        background-color:#2e2d2d;
        color: white;
        font-family: "PT Mono", monospace;
        cursor: pointer;
        box-shadow: 0 3px 3px 0 rgba(0,0,0,.3);
    }
</style>