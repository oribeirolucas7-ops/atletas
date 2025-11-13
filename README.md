# atletas
Verificação notas atletas

let atletas = [
  { nome: "Cesar Abascal", notas: [10, 9.34, 8.42, 10, 7.88] },
  { nome: "Fernando Puntel", notas: [8, 10, 10, 7, 9.33] },
  { nome: "Daiane Jelinsky", notas: [7, 10, 9.5, 9.5, 8] },
  { nome: "Bruno Castro", notas: [10, 10, 10, 9, 9.5] }
];

function calcularMedias(atletas) {
  atletas.forEach(atleta => {
    // Cria uma cópia das notas e ordena
    let notasOrdenadas = [...atleta.notas].sort((a, b) => a - b);

    // Remove a menor e a maior nota
    let notasValidas = notasOrdenadas.slice(1, 4);

    // Calcula a média das notas válidas
    let soma = notasValidas.reduce((acc, nota) => acc + nota, 0);
    let media = soma / notasValidas.length;

    // Exibe os resultados com média formatada em 2 casas decimais
    console.log(`Atleta: ${atleta.nome}`);
    console.log(`Notas Obtidas: ${atleta.notas.join(", ")}`);
    console.log(`Média Válida: ${media.toFixed(2)}\n`);
  });
}

// Executa a função
calcularMedias(atletas);


class Atleta {
        constructor(nome, idade, peso, altura, notas) {
                this.nome = nome;
                this.idade = idade;
                this.peso = peso;
                this.altura = altura;
                this.notas = notas;
                this.categoria = this.calculaCategoria();
                this.imc = this.calculaIMC();
                this.mediaValida = this.calculaMediaValida();
        }

        // Método para calcular a categoria
        calculaCategoria() {
                if (this.idade >= 9 && this.idade <= 11) {
                        return "Infantil";
                } else if (this.idade === 12 || this.idade === 13) {
                        return "Juvenil";
                } else if (this.idade === 14 || this.idade === 15) {
                        return "Intermediário";
                } else if (this.idade >= 16 && this.idade <= 30) {
                        return "Adulto";
                } else {
                        return "Sem categoria";
                }
        }

        // Método para calcular o IMC
        calculaIMC() {
                return this.peso / (this.altura * this.altura);
        }

        // Método para calcular a média válida (desconsiderando menor e maior nota)
        calculaMediaValida() {
                if (this.notas.length <= 2) {
                        return 0; // Não é possível calcular média válida com menos de 3 notas
                }
                const notasOrdenadas = [...this.notas].sort((a, b) => a - b);
                notasOrdenadas.pop(); // Remove a maior nota
                notasOrdenadas.shift(); // Remove a menor nota
                const soma = notasOrdenadas.reduce((acc, nota) => acc + nota, 0);
                return soma / notasOrdenadas.length;
        }

        // Métodos de obtenção de informações
        obtemNomeAtleta() {
                return this.nome;
        }

        obtemIdadeAtleta() {
                return this.idade;
        }

        obtemPesoAtleta() {
                return this.peso;
        }

        obtemAlturaAtleta() {
                return this.altura;
        }

        obtemNotasAtleta() {
                return this.notas;
        }

        obtemCategoria() {
                return this.categoria;
        }

        obtemIMC() {
                return this.imc;
        }

        obtemMediaValida() {
                return this.mediaValida;
        }
}

// Exemplo de uso
const atleta = new Atleta("Cesar Abascal", 30, 80, 1.7, [10, 9.34, 8.42, 10, 7.88]);

console.log("Nome:", atleta.obtemNomeAtleta());
console.log("Idade:", atleta.obtemIdadeAtleta());
console.log("Peso:", atleta.obtemPesoAtleta());
console.log("Altura:", atleta.obtemAlturaAtleta());
console.log("Notas:", atleta.obtemNotasAtleta().join(","));
console.log("Categoria:", atleta.obtemCategoria());
console.log("IMC:", atleta.obtemIMC());
console.log("Média válida:", atleta.obtemMediaValida());

