<template>
  <div class="about">
    <h1>Min</h1>
    <input v-model="minA">
    <input v-model="minB">
    <button v-on:click="min()">Min</button>
    {{ minAnswer }}
    <h1>Max</h1>
    <input v-model="maxA">
    <input v-model="maxB">
    <button v-on:click="max()">Max</button>
    {{ maxAnswer }}
    <h1>Abs</h1>
    <input v-model="abs">
    <button v-on:click="abs1()">Abs</button>
    {{ absAnswer }}
    <h1>isEven</h1>
    <input v-model="isEven">
    <button v-on:click="isEven1()">isEven</button>
    {{ isEvenAnswer }}
    <h1>Min3</h1>
    <input v-model="min1A">
    <input v-model="min1B">
    <input v-model="min1C">
    <button v-on:click="min3()">min3</button>
    {{ min3Answer }}
    <h1>Max3</h1>
    <input v-model="max1A">
    <input v-model="max1B">
    <input v-model="max1C">
    <button v-on:click="max3()">max3</button>
    {{ max3Answer }}
  </div>
</template>

<script>
function min() {
  if (this.minA < this.minB) {
    this.minAnswer = this.minA;
  } else {
    this.minAnswer = this.minB;
  }
}

function max() {
  if (this.maxA < this.maxB) {
    this.maxAnswer = this.maxA;
  } else {
    this.maxAnswer = this.maxB;
  }
}

function abs() {
  if (this.abs < 0) {
    this.absAnswer = this.abs * -1
  } else {
    this.absAwnswer = this.abs
  }
}

function isEven() {
  if (this.isEven % 2 == 0) {
    this.isEvenAnswer = true;
  } else {
    this.isEvenAsnwer = false;
  }
}

function min3() {
  if (this.min1A < this.min1B && this.min1A < this.min1C) {
    this.min3Answer = this.min1A;
  } else if (this.min1B < this.min1A && this.min1B < this.min1C) {
    this.min3Answer = this.min1B;
  } else {
    this.min3Answer = this.min1C;
  }
}

function max3() {
  if (this.max1A >= this.max1B && this.max1A >= this.max1C) {
    this.max3Answer = this.max1A;
  } else if (this.max1B >= this.max1A && this.max1B >= this.max1C) {
    this.max3Answer = this.max1B;
  } else {
    this.max3Answer = this.max1C;
  }
}

export default {
  data: function () {
    return {
      'minA': 0,
      'minB': 0,
      'minAnswer': 0,
      'maxA': 0,
      'maxB': 0,
      'maxAnswer': 0,
      'abs': 0,
      'absAnswer': 0,
      'isEven': 0,
      'isEvenAnswer': 0,
      'min1A': 0,
      'min1B': 0,
      'min1C': 0,
      'min3Answer': 0,
      'max1A': 0,
      'max1B': 0,
      'max1C': 0,
      'max3Answer': 0
    }
  },

  methods: {
    'min': min,
    'max': max,
    'abs1': abs,
    'isEven1': isEven,
    'min3': min3,
    'max3': max3
  }
}
</script>
