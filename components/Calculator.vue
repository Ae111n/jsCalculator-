<template>
    <div id="container">
        <h1 class="title">FCC Calculator</h1>
        <div id="calculator">
            <div id="display"></div>
            <div id="keypad">
                <button id="pad" class="button ac">AC</button>
                <button id="pad" class="button">/</button>
                <button id="pad" class="button">x</button>
                <button id="pad" class="button">7</button>
                <button id="pad" class="button">8</button>
                <button id="pad" class="button">9</button>
                <button id="pad" class="button">-</button>
                <button id="pad" class="button">4</button>
                <button id="pad" class="button">5</button>
                <button id="pad" class="button">6</button>
                <button id="pad" class="button">+</button>
                <button id="pad" class="button">1</button>
                <button id="pad" class="button">2</button>
                <button id="pad" class="button">3</button>
                <button id="pad" class="button equal">=</button>
                <button id="pad" class="button zero">0</button>
                <button id="pad" class="button">.</button>

            </div>
        </div>
    </div>
</template>

<script>
export default {

}
</script>

<style>
* {
    margin: auto;
}

.title {
    border: 1px solid green;
    margin-top: 100px;
}

#container {
    display: flex;
    flex-direction: column;
    border: 2px solid grey;
    height: 100vh;
}

#calculator {
    border: 3px solid black;
    height: 600px;
}

#display {
    border: 2px solid blue;
    height: 90px
}

#keypad {
    height: 505px;
    width: 400px;
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 1px;



}

.button {
    padding: 20px;
    font-size: 28px;
    text-align: center;
    border: 1px solid #ccc;
    background-color: #555;
    color: rgb(255, 255, 255);
    cursor: pointer;
    width: 100%;
    height: 100%;
    border-radius: 3px;
}

.button.ac {
    background-color: #b23b3b;
    grid-column: span 2;
}

.button.equal {
    background-color: #234c78;
    grid-row: span 2;
}

.button.zero {
    grid-column: span 2;
}
</style>