<script>
  export default {
    name: 'App',
    data() {
    return {
      a: 0,
      b: 0,
      operacao: 'soma',
      resultado: 0
    };
  },
  methods: {
  calcular() {
    switch (this.operacao) {
    case 'soma':
      this.resultado = this.a + this.b;
    break;
    case 'subtracao':
      this.resultado = this.a - this.b;
    break;
    case 'multiplicacao':
      this.resultado = this.a * this.b;
    break;
    case 'divisao':
      this.resultado = this.b !== 0 ? this.a / this.b : 'Indefinido';
    break;
    case 'quadrado':
      this.resultado = Math.pow(this.a, 2);
    break;
    case 'cubo':
      this.resultado = Math.pow(this.a, 3);
    break;
    case 'raizQuadrada':
      this.resultado = Math.sqrt(this.a);
    break;
    case 'porcentagem':
      this.resultado = this.a * (this.b / 100);
    break;
    default:
      this.resultado = 0;
    }
  },
}
};
</script>
<template>
  <div id="app" class="container">
    <h1 class="mt-4 mb-3 text-center">Calculadora Aritmética</h1>
    <div class="row justify-content-center">
      <div class="col-md-4">
        <input type="number" class="form-control" v-model.number="a" @input="calcular">
      </div>
      <div class="col-md-4">
        <select class="form-control" v-model="operacao" @change="calcular">
          <option value="soma">+</option>
          <option value="subtracao">-</option>
          <option value="multiplicacao">*</option>
          <option value="divisao">/</option>
          <option value="quadrado">x²</option>
          <option value="cubo">x³</option>
          <option value="raizQuadrada">√</option>
          <option value="porcentagem">%</option>
        </select>
      </div>
      <div class="col-md-4">
        <input type="number" class="form-control" v-model.number="b" @input="calcular" v-if="operacao !== 'raizQuadrada' && operacao !== 'cubo' && operacao !== 'quadrado'">
      </div>
    </div>
    <div class="row justify-content-center mt-3">
      <button class="btn btn-primary btn-width">Resultado: <strong>{{ resultado }}</strong></button>
    </div>
  </div>
</template>


<style scoped>
.btn-width {
  width: 150px; /* Defina a largura desejada para o botão */
}
</style>
