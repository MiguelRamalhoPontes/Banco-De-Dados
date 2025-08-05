# Banco de Dados Relacional, Não Relacional e Normalização
![](https://hostbits.com.br/blog/wp-content/uploads/2022/03/banco-de-dados-1024x538.jpg)
### Banco de Dados
````
Antes de tudo precisamos entender o que é banco de dados no geral, os bancos de dados são usados para armazenar e organizar dados,
de modo que seja mais fácil gerenciá-los e acessá-los. À medida que uma coleção de dados cresce e ganha mais complexidade,
torna-se mais difícil manter os dados organizados, acessíveis e protegidos.
````
---
### Banco de Dados Relacional
```
Um banco de dados relacional é um tipo de banco de dados que organiza dados em tabelas, com linhas e colunas, onde cada linha
representa um registro e cada coluna representa um atributo. Ele usa relações entre essas tabelas para conectar
e recuperar informações relacionadas, facilitando a consulta e análise de dados.

Alguns exemplos incluem sistemas de gestão empresarial (ERP), comércio eletrônico, sistemas de gerenciamento de conteúdo
e sistemas de relacionamento com o cliente (CRM)
```
### Banco de Dados Não Relacional
````
Um banco de dados não relacional, também conhecido como NoSQL (Not Only SQL), é um tipo de sistema de gerenciamento de banco de 
dados que não utiliza o modelo tradicional de tabelas com linhas e colunas para armazenar dados, como os bancos de dados
relacionais. Em vez disso, eles empregam modelos de dados mais flexíveis e adaptáveis, como chave-valor, documentos, 
colunas largas ou gráficos, para lidar com grandes volumes de dados não estruturados ou semiestruturados.

Exemplos de uso incluem: plataformas de streaming, aplicativos de jogos, redes sociais, IoT e sistemas de gerenciamento de
conteúdo. 
````
---
### Normalização
````
Normalização é o processo de estabelecer regras, diretrizes ou características comuns para atividades, produtos ou serviços,
visando a padronização e a otimização em um determinado contexto. Seu objetivo principal é promover a ordem,
facilitar a comunicação, reduzir custos e aumentar a eficiência em diversas áreas.
````
---
### Exemplo de Tabela Não Normalizada 
| Pedido_ID | Cliente_Nome | Cliente_Endereço | Produto_ID | Produto_Nome | Quantidade | Preço_Total | 
|----------|--------------|---------------|----------|------------|----------|-----------|
|1|João Silva|Rua A,123|10|Caneta|2|4,00|
|1|João Silva|Rua A,123|11|Lápis|1|2,00|
|2|Maria Souza|Rua B,456|10|Caneta|5|10,00|
---


## Normalização até a 3° Forma Normal
#### Primeira Forma (1FN)
- Elimina campos com varios valores em um mesmo registro, garantindo que os dados estejam bem organizados.
Como por exemplo: você esta criando uma tabela com informaçoes de pedidos de clientes, e um cliente comprou varios produtos de uma vez se colocar todos os prudotos em um unico campo ficaria (Produtos: Calsa, Camisa, Blusa, Tenis), ficaria confuso para pesquisar e organizar os dados, então o 1FN arruma isso colocando cada protudo com seu valor em cada campo.

#### Segunda Forma (2FN)
- Depois que os dados estão organizados com um valor por campo (1FN), o próximo passo é garantir que cada informação esteja no lugar certo e ligada à chave correta. 
- Exemplo: Você tem uma tabela de pedidos. Nela, você colocou o nome e o endereço do cliente repetidos em cada linha de pedido. Mas essas informações não fazem parte do pedido em si, isso é um problema, porque o cliente pode mudar de endereço, você teria que atualizar várias linhas iguais, para solucionar o 2FN cria uma tabela para os dados do cliente e uma tabela para os pedidos, evitando a confusão.

#### Terceira Forma (3FN)
- Depois de organizar bem os dados com a 1FN e 2FN, na 3FN o objetivo é evitar informações repetidas ou desnecessárias, principalmente aquelas que podem ser calculadas ou que dependem de outra informação que já está na tabela.
- Exemplo: Você tem um item de pedido com os campos: Produto, Quantidade, Preço, Total. Mas o Preço Total = Preço × Quantidade, Então não precisamos guardar o Preço Total na tabela porque ele já pode ser calculado com os dados que já temos, se guardarmos esse valor, corremos o risco de ele ficar errado se alguém mudar a quantidade ou o preço, para resolver o 3FN cria uma tabela dos produtos com o preço de cada produto e uma tabela para os itens, que guarda qual produto foi comprado e em qual quantidade.
---
## Estrutura não relacionada *(formato JSON)*

```JSON
{
  "pedido_id": 1,
  "cliente": {
    "nome": "Lucas",
    "endereco": "Rua LogoAli, 31"
  },
  "itens": [
    {
      "produto_id": 52,
      "nome": "Teclado Gamer",
      "quantidade": 1,
      "preco_total": 250.00
    },
    {
      "produto_id": 65,
      "nome": "Mouse Gamer",
      "quantidade": 1,
      "preco_total": 200.00
    }
  ]
}
```

Em bancos de dados relacionais, a normalização evita redundâncias e organiza os dados em múltiplas tabelas. Porém, isso requer diversas operações para reunir os dados, o que pode impactar o desempenho em consultas simples ou frequentes.

Já em modelos não relacionais, como o formato **JSON:**
- Dados relacionados estão agrupados: Informações do cliente e itens estão juntos no mesmo documento, sem a necessidade de tabelas separadas.
- Consulta direta e mais rápida: Ideal para aplicações que acessam o pedido completo com frequência.
- Flexibilidade de estrutura: Permite armazenar campos variáveis sem alterar o esquema geral.































