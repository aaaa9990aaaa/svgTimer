<template>
    <div class="wd_input">
        <input :type="type" v-model="data" @input="inputHandle" :autocomplete="autocomplete" :placeholder="placeholder">
    </div>
</template>

<script>
export default {
    props: {
        'value': {
            type: Number|String,
            default: ''
        },
        type: {
            type: String,
            default: 'text'
        },
        autocomplete: {
            type: String,
            default: 'off'
        },
        placeholder: {
            type: String,
            default:'请输入'
        }
    },
    data() {
        return {
            data: this.value
        }
    },
    methods: {
        inputHandle() {
            this.$emit('input',this.data)
        }
    }
}
</script>

<style scoped lang="scss">
    .wd_input {
        position: relative;
        font-size: 1.1rem;
        display: inline-block;
        width: 100%;
        input {
            border-radius: 4px;
            border: 1px solid #497FFF;
            background-color: transparent;
            box-sizing: border-box;
            color: #CCCCCC;
            display: inline-block;
            font-size: inherit;
            height: 3rem;
            line-height: 3rem;
            outline: none;
            padding: 0 1rem;
            transition: border-color 0.2s cubic-bezier(0.645, 0.045, 0.355, 1);
            width: 100%;
            &:focus {
                border-color: #fff;
            }
        }
    }
</style>