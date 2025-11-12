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
