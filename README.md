Projeto de fundamentos do nodeJs da Rocketseat

Segundo módulo aborda o conceito de streams, que provavelmente foi o principal motivo do nodeJs ser do tamanho que é hoje.

# Streams
No Node.js são uma maneira eficiente de manipular grandes quantidades de dados de forma contínua e controlada. Eles permitem processar dados de forma incremental, sem precisar carregar tudo na memória de uma vez, o que é especialmente útil para operações de leitura e gravação de arquivos grandes, manipulação de dados de rede, e transferência de arquivos. 

## Tipos de Streams: 
- Readable (legíveis): Streams dos quais você lê dados, como o conteúdo de um arquivo, entrada de rede ou resposta HTTP. Exemplo: fs.createReadStream().
- Writable (graváveis): Streams para onde você grava dados, como arquivos de saída ou um request HTTP. Exemplo: fs.createWriteStream().
- Duplex: Streams que podem ser lidos e gravados, como sockets de rede que recebem e enviam dados simultaneamente. Exemplo: net.Socket.
- Transform: Streams que modificam ou transformam os dados enquanto eles são lidos ou gravados, como a compressão de dados. Exemplo: zlib.createGzip().

## Eventos Principais dos Streams
- data: Emitido quando novos dados estão disponíveis em um stream legível.
- end: Emitido quando todos os dados foram lidos em um stream legível.
- error: Emitido se um erro ocorre durante a operação.
- finish: Emitido quando todos os dados foram gravados em um stream gravável.


## Exemplo de Uso com fs
```
const fs = require('fs');
// Criando streams de leitura e escrita
const readable = fs.createReadStream('input.txt');
const writable = fs.createWriteStream('output.txt');

// Copiando dados do arquivo de entrada para o arquivo de saída
readable.pipe(writable);

writable.on('finish', () => {
  console.log('Arquivo copiado com sucesso!');
});
```