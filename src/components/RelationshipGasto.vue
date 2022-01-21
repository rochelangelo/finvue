<template>
 <div id="listContainer">
    <RelationshipItem v-for="dado in dados" :key="dado.id"
        :reference="dado.reference"
        :type="dado.type"
        :category="dado.category"
        :value="dado.value"
    />
 </div>
</template>

<script>
import RelationshipItem from "./RelationshipItem.vue"

export default {
    name: "Relationship",
    components: {
        RelationshipItem,
    },
    data: () => ({
        data: []
    }),
    props: {
        dados: null
    },
    methods: {
        
    }
}
</script>
<style scoped>
#listContainer{
    margin: 0 auto;
    padding-top: 10px;
}
</style>