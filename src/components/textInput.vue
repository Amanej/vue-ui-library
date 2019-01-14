<template>
    <label>
        <input 
            :class="{changed: changed}"
            :style="customCSS"
            type="text" 
            name="textInput"
            v-on:keyup.enter="saveInput" 
            :placeholder="placeholder" 
            v-model="value"
            ref="textInput"
        />
    </label>
</template>

<script>
/* eslint-disable */
export default {
    name: 'textInput',
    created: function() {
        //console.log('initialValue ',this.initialValue);
        this.value = this.initialValue;
    },
    computed: {
        customCSS() {
            if(this.customStyle) {
                return this.customStyle
            }
        },
        changed() {
            return this.value !== this.init
        }
    },
    methods: {
        saveInput(e) {
            //console.log(e);
            this.$refs.textInput.blur();
            this.init = this.value;
        }
    },
    props: {
        placeholder: {
            default: 'Enter your info',
            type: String,
            required: false
        },
        initialValue: {
            type: String,
            required: true
        },
        customStyle: {
            type: Object,
            required: false
        },
        changedStyle: {
            type: Object,
            required: false
        }
    },
    data: () => {
        return (
            {
                init: '',
                value: ''
            }
        )
    }
}
</script>

<style lang="scss">
label {
    min-width:                  250px;
    transition:                 0.4s;
    input {
        //padding:                5px;
        font-size:              16px;
        padding:                12px;
        min-width:              250px;
        transition:             0.4s;
        border:                 1px solid lightgrey;
        &.changed {
            color: red;
        }
        &:focus {
            outline: none;
        }
    }
}
</style>
