
<script setup>
const props = defineProps({
    head: {
        type: Array,
        required:false
    },
    columnTemplates: {
        type: String,
        required:false
    }
})

</script>


<template>
    <div class="table-wrapper">
        <div class="table">
            <div 
            class="table-head"
            :style="{'grid-template-columns': columnTemplates}"
            >
                <div 
                class="table-head__name"
                v-for="(element, i) of head"
                :key="i"
                >
                {{ element }}
                </div>
            </div>
            <slot></slot>
        </div>
    </div>
</template>



<style lang="scss" scoped>
.table {
    width: 100%;
    margin-bottom: 40px;
    margin-top: 15px;
    &-wrapper {
        display: flex;
        justify-content: center;
    }
    &-head {
        padding: 5px 16px;
        display: grid;
        column-gap: 10px;
        align-items: center;
        border-bottom: 2px solid #dadada;
        &__name {
            display: flex;
            justify-content: flex-start;
            align-items: center;
            color: #2c2c2c;
            cursor: pointer;
        }
    }
}
</style>