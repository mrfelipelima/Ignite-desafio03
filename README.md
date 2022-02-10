# Desafio 03 - Ignite

Created: February 4, 2022 6:23 PM

Essa API tem basicamente a função de cadastrar uma lista de repositórios e então será possível dar likes nos repositórios cadastrados. O desafio consistia em debugar e refatorar o código da API para que ela passasse em alguns testes, de acordo [com as instruções](https://www.notion.so/Desafio-03-Corrigindo-o-c-digo-c15c8a2e212846039a367cc7b763c6dd).

Tenho alguns comentários pertinentes a esse desafio: passei algumas horas para resolver sozinho, e isso envolveu muita pesquisa e dedicação para resolução do problema. Resolvi quase todos os problemas da API para que ela passasse nos testes, restando apenas revisar a rota PUT no /repositories onde eu deveria implementar uma função para que não fosse possível editar a quantidade de likes de um repositório através desse endpoint. Depois de *bater cabeça* tentando encontrar a melhor forma de implantar a solução resolvi editar o código mesmo sabendo que não ia dar certo, e para minha surpresa, os testes passaram:

![Untitled](Desafio%2003%20-%20Ignite%20cfb7419a41f04250b21a4323a445b2ec/Untitled.png)

Eu fiquei perplexo, pois eu estava apenas “descontraindo” depois de passar horas pesquisando como resolver aquele desafio. E eu imediatamente pensei que aquilo não podia ser possível e que precisava testar manualmente. Realizei a edição dos dados no PUT e pedi a lista no GET, os dados foram sobrescritos, restando apenas as informações que passei no PUT, se observarem o segundo item da resposta não segue o padrão da API:

![Untitled](Desafio%2003%20-%20Ignite%20cfb7419a41f04250b21a4323a445b2ec/Untitled%201.png)

A brincadeira que fiz no código foi basicamente passar para o respectivo item, os dados que eu recebesse no corpo da requisição, ignorando apenas o likes, caso esse fosse enviado:

![Untitled](Desafio%2003%20-%20Ignite%20cfb7419a41f04250b21a4323a445b2ec/Untitled%202.png)

Aí caiu a ficha: o pessoal da Rocketseat esqueceu de incluir essa possibilidade no teste automático, pois o pedido era bem claro: **Lembre-se de manter as informações que não foram passadas pelo corpo**:

![Untitled](Desafio%2003%20-%20Ignite%20cfb7419a41f04250b21a4323a445b2ec/Untitled%203.png)

Tive que interromper o desafio pois me dei conta que eu já estava atrasado para o meet do Ignite Nitro. Quando voltei da palestra da [Jake](https://github.com/jakeliny) com a mente mais calma, eu só criei um *if* para verificar se algum valor de likes fosse passado no *body* da requisição e deletava ele antes de adicionar os dados no *array*.

![Untitled](Desafio%2003%20-%20Ignite%20cfb7419a41f04250b21a4323a445b2ec/Untitled%204.png)

GG, usei essa referência do MDN para lembrar que eu poderia trabalhar com o objeto antes de passar ele para o *array*.

[delete operator - JavaScript | MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/delete)

E com isso eu concluí os três primeiros desafios da trilha de Node.JS do Ignite! Momento [full dopamina](https://www.youtube.com/watch?v=OMm1RLF32ig)!

![Untitled](Desafio%2003%20-%20Ignite%20cfb7419a41f04250b21a4323a445b2ec/Untitled%205.png)