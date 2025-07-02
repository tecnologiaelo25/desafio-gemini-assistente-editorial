# Desafio Grupo Elo Editorial: Assistente de Publicações com Gemini API

Olá, dev\! O **Grupo Elo Editorial** te dá as boas-vindas ao nosso desafio de desenvolvimento.

Buscamos pessoas inovadoras para nos ajudar a conectar nossos autores e livros com o público leitor de formas criativas. Este desafio foi desenhado para avaliar suas habilidades na construção de um agente conversacional moderno, utilizando a **API do Google Gemini** e seu poderoso recurso de **Function Calling**.

Todo o material de que você precisa para começar está neste repositório.

## Visão Geral do Desafio

Você irá construir um **"Assistente de Publicações"**, um chatbot que será o ponto de contato digital do nosso grupo editorial. Ele fornecerá informações sobre os títulos publicados pelos nossos selos, **Elo Editora** e **Perabook**, e ajudará os leitores a encontrarem nossos livros.

## O Cenário

Sua missão é criar um assistente virtual que possa ser integrado ao nosso futuro site. Este assistente deve ser capaz de realizar duas funções essenciais para nossos leitores e parceiros comerciais:

1.  **Fornecer informações detalhadas** sobre qualquer livro publicado por nós (data de lançamento, selo, sinopse).
2.  **Ajudar o leitor a encontrar** em quais livrarias (físicas ou online) nossos livros estão sendo vendidos.

## O Desafio Técnico

Você desenvolverá uma aplicação ou script que implemente um chat com a API do Gemini. A essência do desafio está em usar o `function calling` para que o assistente possa consultar informações e executar ações baseadas no nosso catálogo.

### Requisitos Funcionais

1.  **Conversa com Contexto:** O chat deve manter o histórico das interações para criar uma experiência fluida e natural. Se um usuário perguntar sobre um livro e depois onde comprá-lo, o assistente deve lembrar do livro em questão.

2.  **Uso de Ferramentas (Function Calling):** Você deve definir e registrar as seguintes "ferramentas" para o modelo do Gemini:

      * **Obter Detalhes do Livro**

          * **Nome da função:** `get_book_details`
          * **Parâmetros:** `book_title: string`
          * **Retorno esperado:** Um objeto contendo a data de lançamento, o selo editorial e a sinopse do livro.

      * **Encontrar Pontos de Venda**

          * **Nome da função:** `find_stores_selling_book`
          * **Parâmetros:** `book_title: string`, `city: string` (opcional)
          * **Retorno esperado:** Um objeto contendo uma lista de nomes de livrarias.
          * **Nota:** Se o parâmetro `city` não for fornecido, a função deve retornar a lista de lojas online.

3.  **Execução das Funções:** Sua aplicação deve ser capaz de receber a solicitação de `function call` do Gemini, executar a função correspondente em seu código (consultando os dados do `mock_catalog.json`) e retornar o resultado para o modelo.

### Exemplo de Fluxo de Interação

> **Usuário:** Olá, gostaria de saber mais sobre o livro "A Revolução dos Bichos".

> **Assistente:** Claro\! "A Revolução dos Bichos", de George Orwell, é uma obra publicada pelo nosso selo **Perabook**. É uma fábula satírica poderosa sobre totalitarismo. Posso te ajudar a encontrar onde comprá-lo?

> **Usuário:** Sim, por favor\! Onde encontro em São Paulo?

> **Assistente:** Em São Paulo, você encontra "A Revolução dos Bichos" na Livraria da Vila, na Livraria Leitura e na Livraria Cultura. Ele também está disponível em várias lojas online.

## Como Entregar sua Solução

Queremos focar na sua lógica e criatividade, não na complexidade do ambiente. Por isso, a entrega é flexível.

  * **Opção 1: Repositório no GitHub (Recomendado)**

      * Crie um repositório público na sua conta.
      * Adicione seu código (pode ser um script simples ou um projeto mais estruturado).
      * Crie um `README.md` claro, explicando a linguagem utilizada e as **instruções de como configurar e executar sua solução**.
      * Inclua um arquivo `.env.example` para indicar as variáveis de ambiente necessárias (como a `GEMINI_API_KEY`).

  * **Opção 2: Google Colab ou Notebook Similar**

      * Crie um notebook público (Google Colab, Jupyter Notebook, etc.).
      * Estruture o notebook com células de texto (Markdown) para explicar sua lógica e células de código executáveis.
      * Garanta que haja instruções claras sobre como o avaliador deve adicionar a API Key para poder executar o notebook (ex: usando o gerenciador de "Secrets" do Colab).

**Ao finalizar, envie o link público do seu repositório ou notebook para nós.**

## Critérios de Avaliação

1.  **Funcionalidade:** A solução atende aos requisitos? O fluxo de `function calling` está correto e completo?
2.  **Clareza e Lógica do Código:** Seu código é limpo, legível e fácil de entender?
3.  **Qualidade da Documentação:** Suas instruções no `README.md` ou no notebook são claras o suficiente para que possamos rodar sua solução sem dificuldades?
4.  **Boas Práticas:** Você demonstrou cuidado com a segurança da API Key, não a expondo diretamente no código?

## Para Começar: Recursos e Dados

### Recursos Úteis

  * **Documentação do Gemini:** [Página Principal](https://ai.google.dev/gemini-api/docs)
  * **Guia de Function Calling (Essencial):** [Function Calling Guide](https://ai.google.dev/gemini-api/docs/function-calling)
  * **Quickstarts:** [Python](https://ai.google.dev/gemini-api/docs/get-started/python) | [JavaScript/Node.js](https://www.google.com/search?q=https://ai.google.dev/gemini-api/docs/get-started/javascript)
  * **Google Colab:** [colab.research.google.com](https://colab.research.google.com)

### Dados do Desafio (`mock_catalog.json`)

Você deve usar este catálogo de dados fictício como sua "base de dados".

\<details\>
\<summary\>Clique para ver o conteúdo do mock\_catalog.json\</summary\>

```json
{
  "books": [
    {
      "title": "A Revolução dos Bichos",
      "author": "George Orwell",
      "imprint": "Perabook",
      "release_date": "17/08/1945",
      "synopsis": "Uma fábula satírica na qual os animais de uma fazenda, cansados da exploração humana, se rebelam. Liderados por porcos inteligentes, eles buscam criar uma sociedade utópica de igualdade, mas acabam caindo sob uma nova e mais brutal tirania.",
      "availability": {
        "São Paulo": ["Livraria da Vila", "Livraria Leitura", "Livraria Cultura"],
        "Rio de Janeiro": ["Livraria Travessa"],
        "Online": ["Amazon.com.br", "Magazine Luiza", "Loja Elo Editorial"]
      }
    },
    {
      "title": "O Pequeno Príncipe",
      "author": "Antoine de Saint-Exupéry",
      "imprint": "Elo Editora",
      "release_date": "06/04/1943",
      "synopsis": "Um piloto cai com seu avião no deserto do Saara e ali encontra um menino de cabelos dourados vindo de outro planeta. Através de suas conversas, o livro explora temas como amor, perda, amizade e a natureza humana.",
      "availability": {
        "São Paulo": ["Livraria Cultura", "Livraria da Vila"],
        "Belo Horizonte": ["Livraria Leitura"],
        "Curitiba": ["Livrarias Curitiba"],
        "Online": ["Amazon.com.br", "Americanas.com", "Livraria da Vila (Online)"]
      }
    },
    {
      "title": "Dom Casmurro",
      "author": "Machado de Assis",
      "imprint": "Elo Editora",
      "release_date": "01/06/1899",
      "synopsis": "Narrado pelo próprio Bentinho, o romance conta a história de seu amor por Capitu e o ciúme que corrói sua vida, levantando a eterna dúvida sobre a traição da amada com seu melhor amigo, Escobar. Uma obra-prima da literatura brasileira.",
      "availability": {
        "São Paulo": ["Livraria da Vila", "Livraria Cultura"],
        "Rio de Janeiro": ["Livraria Travessa", "Livraria Leitura"],
        "Online": ["Amazon.com.br", "Estante Virtual"]
      }
    },
    {
      "title": "Inteligência Artificial: Guia para o Futuro",
      "author": "Dr. Ada Turing",
      "imprint": "Perabook",
      "release_date": "15/09/2025",
      "synopsis": "Um olhar profundo e acessível sobre o futuro da inteligência artificial, explorando seu impacto na sociedade, na ética e no mercado de trabalho. Um guia essencial para entender a próxima grande revolução tecnológica.",
      "availability": {
        "Online": ["Amazon.com.br (Pré-venda)", "Loja Elo Editorial (Pré-venda)"]
      }
    }
  ]
}
```

\</details\>

\<br\>

A equipe do **Grupo Elo Editorial** deseja boa sorte\! Estamos ansiosos para ver o que você vai construir.
