<template>
    <pre>modelValue: {{ JSON.stringify(vmodel) }}</pre>
    <vue-select v-model="vmodel"
                :options="options"
                @update:modelValue="updateSelectValue"
    >
        <template #label="{ selected }">
            <template v-if="selected">
                <div class="option">
                    <div class="image">
                        <img :src="selected.image">
                    </div>
                    <div class="text">
                        {{ selected.label }}
                    </div>
                </div>
            </template>
            <template v-else>
                Select option
            </template>
        </template>

        <template #dropdown-item="{ option }">
            <div class="option">
                <div class="image">
                    <img :src="option.image">
                </div>
                <div class="text">
                    {{ option.label }}
                </div>
            </div>
        </template>
    </vue-select>
</template>

<script>
    import { defineComponent, ref } from 'vue';
    import VueNextSelect from 'vue-next-select';

    export default defineComponent({
        components: {
            'vue-select': VueNextSelect,
        },

        props: {
            options: Object,
        },

        emits: [
            'updateSelectValue',
        ],

        setup(props, { emit }) {
            const vmodel = ref(null);
            const options = props.options;

            const updateSelectValue = () => {
                emit('updateSelectValue', vmodel)
            }

            return {
                updateSelectValue,
                vmodel,
            }
        }
    })
</script>

<style lang="scss" scoped>
  @import "../../css/components/vue-select";
</style>
