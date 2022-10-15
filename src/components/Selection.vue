<template>
    <div class="selection__block">
        <div class="selection__top">
            <div @click="removeItem(item)" class="selection__item" v-for="item in selectedItems" :key="item.id">
                <span>{{ item.name }}</span>
            </div>
            <span class="counter" v-if="counter">{{ selectedItems.length }}/{{ maxItems }}</span>
        </div>
        <div class="selection__bottom">
            <div @click="selectItem(item)" class="selection__item" v-for="item in items" :key="item.id">
                <span>{{ item.name }}</span>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        props: {
            items: Array,
            maxItems: {
                type: Number,
                default: 6
            },
            counter: {
                type: Boolean,
                default: false
            }
        },
        data() {
            return {
                selectedItems: []
            }
        },
        methods: {
            selectItem(item) {
                if (this.maxItems === this.selectedItems.length) return

                this.selectedItems.push(item)
            },
            removeItem(item) {
                this.selectedItems.splice(this.selectedItems.indexOf(item), 1)
            }
        }
    }
</script>