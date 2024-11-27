<template>
    <div id="container">
        <h1 class="title">FCC Calculator</h1>
        <div id="calculator">
            <div id="display1">{{ display1 }}</div>
            <div id="display2">{{ display2 }}</div>
            <div id="keypad">
                <button id="pad" @click="clear" class="button ac">AC</button>
                <button id="pad" @click="push('/')" class="button">/</button>
                <button id="pad" @click="push('*')" class="button">*</button>
                <button id="pad" @click="push('7')" class="button">7</button>
                <button id="pad" @click="push('8')" class="button">8</button>
                <button id="pad" @click="push('9')" class="button">9</button>
                <button id="pad" @click="push('-')" class="button">-</button>
                <button id="pad" @click="push('4')" class="button">4</button>
                <button id="pad" @click="push('5')" class="button">5</button>
                <button id="pad" @click="push('6')" class="button">6</button>
                <button id="pad" @click="push('+')" class="button">+</button>
                <button id="pad" @click="push('1')" class="button">1</button>
                <button id="pad" @click="push('2')" class="button">2</button>
                <button id="pad" @click="push('3')" class="button">3</button>
                <button id="pad" @click="result" class="button equal">=</button>
                <button id="pad" @click="push('0')" class="button zero">0</button>
                <button id="pad" @click="push('.')" class="button">.</button>
            </div>
        </div>
    </div>
</template>

<script>

export default {

    data() {
        return {
            display1: '0',
            display2: ''
        }
    },

    methods: {
        clear() {
            this.display1 = '0'
            this.display2 = ''
        },

        push(n) {
            const operators = ['+', '-', '*', '/', '.'];

            if (this.display1 === '0' && this.display2 === '' && !operators.includes(n)) {
                this.display1 = n;
                this.display2 += n;
            }

            else if (operators.includes(this.display1.slice(-1)) && operators.includes(n)) {
                return;
            }

            else if (operators.includes(n) && this.display1.split('').includes('=')) {
                this.display1 = this.display1.split('=')[1] + n;
                this.display2 = n;
            }

            else if (this.display1.split('').includes('=') && !operators.includes(n)) {
                this.display1 = n;
                this.display2 = n;
            }

            else {
                this.display1 += n;
                this.display2 = n;
            }

        },


        result() {
            try {
                this.display2 = eval(this.display1)
                this.display1 = this.display1 + '=' + eval(this.display1)
            } catch (error) {
                this.display2 = 'ERROR'
            }

        }

    }
}
</script>

<style>
* {
    margin: auto;
    background-color: rgba(43, 160, 46, 0.747);
    font-family: orbitron;
}

.title {
    margin-top: 70px;
    color: black;
    font-size: 40px;
}

#container {
    display: flex;
    flex-direction: column;
    height: 100vh;
}

#calculator {
    border: 5px solid rgb(39, 34, 51);
    border-radius: 5px;
    height: 600px;
    margin-bottom: 40%;
    margin-top: 70px;
    box-shadow: rgba(0, 0, 0, 0.25) 0px 54px 55px, rgba(0, 0, 0, 0.12) 0px -12px 30px, rgba(0, 0, 0, 0.12) 0px 4px 6px, rgba(0, 0, 0, 0.17) 0px 15px 12px, rgba(0, 0, 0, 0.09) 0px -3px 5px;
}

#display1,
#display2 {
    height: 48px;
    font-size: 38px;
    background-color: black;
    color: white;
    width: 400px;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
}


#keypad {
    height: 505px;
    width: 400px;
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 1px;
    background-color: black;
}

.button {
    padding: 20px;
    font-size: 28px;
    text-align: center;
    background-color: #353535;
    color: rgb(255, 255, 255);
    cursor: pointer;
    width: 100%;
    height: 100%;
    border-radius: 2px;
}

.button:hover {
    opacity: 80%;
}

.button.ac {
    background-color: #7a2a2a;
    grid-column: span 2;
}

.button.equal {
    background-color: #212969;
    grid-row: span 2;
}

.button.zero {
    grid-column: span 2;
}
</style>