<template>
    <div class="editor">
        <h2>Inline text editor</h2>
        <button @click="bolden">Bold</button>
        <button @click="italicize">Italic</button>
        <!--
        <div ref="textarea" id="textarea" contenteditable>
            <p>Edit me :)</p>
        </div>
        -->
        <textarea ref="textarea" id="textarea" v-model="input" @blur="setRendered" />

        <!--
        -->
        <h3>Preview</h3>
        <div v-html="input"></div>
        <h3>Preview</h3>
        <div v-html="inputHTMLRendered"></div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            input: '',
            inputHTMLRendered: ''
        }
    },
    methods: {
        getInputInfo() {
            let input = this.input
            const start = this.$refs.textarea.selectionStart
            const end = this.$refs.textarea.selectionEnd
            const text = input.substring(start,end);
            return {
                start: start,
                end: end,
                text: text
            }
        },
        bolden: function () {
            const info = this.getInputInfo();

            const emboldenedText = `<strong>${info.text}</strong>`

            let modifiedText = `${this.input.substring(0,info.start)}${emboldenedText}${this.input.substring(info.end)}`;
            console.log(' modifiedText ',modifiedText);
            modifiedText = this.formatNewLines(modifiedText)
            this.inputHTMLRendered = modifiedText
        },
        italicize: function() {
            const info = this.getInputInfo();
            const emboldenedText = `<i>${info.text}</i>`
            let modifiedText = `${this.input.substring(0,info.start)}${emboldenedText}${this.input.substring(info.end)}`;
            modifiedText = this.formatNewLines(modifiedText)
            this.inputHTMLRendered = modifiedText
        },
        setRendered: function() {
            // Parse text
            let rendered = this.formatNewLines(this.input);
            this.inputHTMLRendered = rendered;
        },
        formatNewLines: function(string) {
            return string.replace(/\n/g, "<br/>")
        }
    }
}
</script>

<style lang="scss" scoped>
div.editor {
    button {
        display: block;
    }
    textarea {
        width: 100%;
        margin: 10px 0;
        min-height: 200px;
    }
}
</style>