---
layout: single
title: "As várias arquiteturas para se fazer jogos. Aqui está o que aprendi."
date: 2025-06-23
last_modified_at: 2025-07-03
header:
  teaser: /assets/images/2025-06-23-as-varias-arquiteturas-para-se-fazer-jogos/teaser.jpg
---

> “No fim do dia, os jogadores só querem se divertir. Mas nós, devs, queremos mais: queremos entender, melhorar e evoluir nosso código.”

---

### 🎮 A motivação: encontrar **a arquitetura ideal**

Durante muito tempo, meu objetivo como desenvolvedor de jogos não era só fazer um jogo divertido. Era também entender **como organizar meu código de forma escalável e fácil de manter**, mesmo quando o escopo começasse a crescer (e sabemos que ele sempre cresce).

Então tive uma ideia: **fazer o mesmo jogo em várias arquiteturas diferentes**, para descobrir qual se encaixava melhor nos seguintes critérios:

- Ser **fácil de manter**
- Ter **escalabilidade**
- Ser bom para **debug**
- Ser **organizado**

Fiz esse experimento algumas vezes. Os dois padrões que mais me agradaram foram:

* **Entity Component System (ECS)**, usando **Flecs**
* **Scriptable Object Architecture**, ou **SOAP**, no Unity

---

### 📚 O acaso encontra o método: Simon Nordon

Recentemente, encontrei os artigos de [Simon Nordon no Medium](https://medium.com/@simon.nordon). E pra minha surpresa, ele teve **a mesma ideia que eu**: desenvolver o mesmo jogo usando diferentes arquiteturas e **comparar o resultado**.

O [estudo de caso sobre *Vampire Survivors*](https://medium.com/@simon.nordon/unity-case-study-vampire-survivors-806eed11bebb) foi simplesmente **fantástico**. Me lembrou muito a estrutura de código dos meus primeiros jogos — como o [Nino Maze Lofi](https://store.steampowered.com/app/1333460/Nino_Maze_LOFI/), claro um belo espaguete.

---

### 🍝 O espaguete pode ser gostoso… até virar indigestão

No artigo ["Desenvolvendo o jogo usando o código espaguete"](https://medium.com/@simon.nordon/unity-architecture-spaghetti-pattern-7e995648c7c8), Simon começa pelo básico: fazer um jogo do jeito mais direto possível, sem grandes preocupações com padrões de arquitetura. Algo que eu mesmo fiz diversas vezes.

E sabe de uma coisa? Funciona.

* Para **projetos pequenos**, é ótimo.
* É **rápido**, **fácil**, e você vê resultados logo.
* E no final do dia, os jogadores não se importam com seu código, e sim com o jogo ser **jogável e divertido**.

Mas, à medida que o projeto cresce…
Modificar algo se torna um pesadelo. Adicionar uma nova feature é como jogar Jenga com nitroglicerina. Foi nesse momento que Simon chega à mesma conclusão que eu: o código espaguete cobra seu preço.

---

### 🧬 Tentando aplicar ECS… sem ECS?

Um dos artigos que mais me surpreendeu foi o da [análise de *Soulstone Survivors*](https://medium.com/@simon.nordon/unity-case-study-soulstone-survivors-1447b7f272c2). Nele, Simon mostra como os desenvolvedores tentaram aplicar ideias de ECS **sem usar um ECS real**.

Isso é interessante porque mostra uma tendência comum: muitos devs querem os benefícios do ECS (composição, performance, separação de responsabilidades), mas sem abrir mão da familiaridade da Unity tradicional.

Resultado? Uma gambiarra híbrida que **não entrega nem a simplicidade da POO, nem a performance do ECS**. E é por isso que, quando bem aplicado, um ECS como o **Flecs** brilha.

---

### ⚙️ GameObject Component Pattern: bonito, mas lento

Outro artigo essencial foi o sobre o [GameObject Component Pattern](https://medium.com/@simon.nordon/unity-architecture-gameobject-component-pattern-34a76a9eacfb). Simon mostra como aplicar um padrão mais limpo e modular usando GameObjects e componentes no estilo Unity padrão.

Só que ele também relata algo que **eu mesmo vivi**:

> “Levei dois meses a mais para finalizar o jogo. Estava exausto.”

Ele conclui com uma frase sensacional:

> “Tinha deixado de usar o código espaguete, mas continuava usando o cérebro espaguete.”

Ou seja: **o problema não era só a arquitetura**, mas *como ele estava abordando a arquitetura*. A mentalidade também precisa mudar, não só o padrão de projeto.

---

### 🧾 Scriptable Object Pattern: potencial subutilizado

O artigo sobre o [Scriptable Object Pattern](https://medium.com/@simon.nordon/unity-architecture-scriptable-object-pattern-0a6c25b2d741) acabou ficando um pouco aquém dos outros. Faltaram métricas e comparações consistentes. Mas ainda assim, traz bons insights.

O uso de ScriptableObjects resolve muitos problemas comuns, como o abuso de Singletons. É **fácil de usar**, funciona bem com designers, e torna o sistema **mais modular**.

Mas há **desvantagens claras**:

* Cria uma **quantidade enorme de arquivos** no projeto.
* Muito precisa ser feito **manualmente no editor**, o que pode ser cansativo e propenso a erro.

Mesmo assim, SOAP ainda é uma das arquiteturas mais promissoras que usei.

---

### 🤷‍♂️ Faltou o mais importante: ECS de verdade

Senti falta de um artigo do Simon abordando o uso **real de ECS**, com métricas e estrutura comparável. Seria muito interessante ver uma análise usando **Flecs**, ou outro sistema de ECS.

Por quê?

Porque **ECS muda tudo**: a forma de pensar, programar, debugar, organizar. Não é só um padrão. É uma **nova mentalidade**. E compará-lo lado a lado com POO, scriptable objects ou código espaguete poderia revelar ainda mais insights para a comunidade.

---

### 🧠 Conclusão: o código importa, sim

Simon tem razão: jogadores não se importam com seu código.

Mas você, como desenvolvedor, **deveria se importar**. Porque é você que vai manter esse código por meses (ou anos). É você que vai debugar às 3 da manhã. É você que vai tentar adicionar um modo cooperativo faltando 1 semana pro lançamento.

E aí, vai querer fazer isso num castelo de cartas?

Pra mim, a resposta tem sido clara:

> **Use código espaguete para protótipos. Use Outro para jogos sérios.**
