<template>
    <FlexboxLayout flexWrap="wrap" backgroundColor="#3c495e" width="100%">
        <TextField class="input-field" v-model="result" editable="false" backgroundColor="#4b5a73" width="100%" height="50" />
        <Button v-for="(number, k) in numbers" @tap="input(number)" :text="number" v-bind:key="k" backgroundColor="#43b883" class="number" />
        <Button v-for="(operation, k) in operations" @tap="input(operation)" :text="operation" v-bind:key="k" backgroundColor="#43b883" class="operation" /> 
        <Button @tap="results()" text="=" backgroundColor="#43b883" width="100%" class="result" />
    </FlexboxLayout>
</template>

<script>
export default {
    data: function() {
        return {
            result: ' ',
            numbers: ['1', '2', '3', '4', '5', '6', '7', '8', '9', '0'],
            operations: ['-', '+', '.', 'C', '*', '/']
        }
    },
    methods: {
        input(up) {
            if(up === 'C')
                this.reset()

            if(this.result == ' ' && this.operations.includes(up, 1) == true)
                this.result = this.result
            else if(this.operations.includes(up, 0) == true && this.operations.includes(this.result.slice(-1), 0) == true)
                this.result = this.result
            else if (up != 'C')
                this.result = this.result + up
        },

        reset() {
            this.result = ' '
        },

        results() {
            if(this.result != ' ')
                this.result = eval(this.result).toString()
        }
    }
}
</script>

<style scoped>

    .input-field {
        height: 30;
        border-radius: 10;
        font-size: 18;
        color: white;
    }

    .number {
        width: 65;
        font-size: 18;
        border-radius: 10;
    }

    .operation {
        width: 65;
        font-size: 18;
        border-radius: 10;
    }

    .result {
        border-radius: 10;
        height: 30;
        font-size: 18;
    }
</style>