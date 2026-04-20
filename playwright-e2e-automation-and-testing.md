# Automação de Testes com Playwright: conteúdo reescrito

## Apresentação

Este conteúdo apresenta uma visão integrada sobre **fundamentos de automação de testes**, **técnicas de projeto de testes de caixa-preta** e **aplicação prática com Playwright** em uma aplicação web de cálculo de descontos. A apresentação original se organiza em dois grandes blocos: um bloco conceitual, voltado à motivação para automação e às técnicas de elaboração de testes, e um bloco prático, dedicado à automação funcional da interface gráfica da Calculadora de Descontos [1].

A partir da apresentação original, do requisito funcional `UC001 - Calcular Desconto de Produto` e da inspeção do sistema disponível publicamente, este documento reescreve este conteúdo de forma mais fluida, didática e tecnicamente precisa, preservando a intenção pedagógica da apresentação e melhorando a redação [1] [2] [3].

## Visão geral deste conteúdo

A proposta central deste conteúdo é mostrar que a automação de testes não deve ser vista apenas como um recurso técnico, mas como uma **estratégia de qualidade**. Este conteúdo progride da motivação para automatizar, passa pelos princípios que orientam uma boa automação, revisita técnicas clássicas de identificação de casos de teste e, por fim, demonstra como esses conceitos podem ser concretizados com Playwright em um sistema web real [1].

| Eixo deste conteúdo | Síntese deste conteúdo | Base principal |
| --- | --- | --- |
| Fundamentos | Por que automatizar, o que automatizar e quais limites considerar | Slides iniciais sobre motivação, candidatos à automação e princípios [1] |
| Projeto de testes | Classes de equivalência, pares ortogonais, tabela de decisão, valores-limite e testes baseados em caso de uso | Slides sobre técnicas de caixa-preta [1] |
| Automação funcional | Conceito de teste funcional automatizado e ferramentas de mercado | Slides sobre testes funcionais automatizados [1] |
| Playwright na prática | Instalação, escrita de testes, locators, ações, asserções, hooks e tempos de espera | Slides finais e documentação oficial [1] [4] [5] |

## 1. Fundamentos da automação de testes

Este conteúdo parte de um problema clássico: **testar manualmente custa tempo, depende de esforço humano contínuo e sofre com variabilidade de execução**. Em outras palavras, quanto mais um sistema evolui, maior tende a ser o custo de retestar funcionalidades para garantir que nada foi quebrado. Essa é a motivação central apresentada no início deste conteúdo: se o software muda continuamente, a repetição de verificações também precisa se tornar escalável [1].

> “O propósito da automação de testes pode ser resumidamente descrito como a aplicação de estratégias e ferramentas tendo em vista a redução do envolvimento humano em atividades manuais repetitivas.” — Cem Kaner, conforme citado na apresentação [1]

A consequência pedagógica dessa definição é importante: **automação não substitui pensamento crítico**. A própria apresentação destaca que ferramenta, isoladamente, não resolve problemas de qualidade. Em termos práticos, isso significa que a utilidade da automação depende da clareza dos requisitos, da qualidade dos casos de teste e da escolha correta dos cenários a automatizar [1].

### 1.1 Automação não elimina o teste manual

Outro ponto importante é que **não se pretende abolir o teste manual**. O teste manual continua essencial para exploração, aprendizagem do produto, avaliação visual, análise contextual e descoberta de problemas inesperados. A automação, por sua vez, é especialmente útil quando o objetivo é repetir verificações com consistência, velocidade e menor custo marginal a cada nova execução [1].

| Comparação | Teste manual | Teste automatizado |
| --- | --- | --- |
| Execução repetitiva | Mais lenta e mais custosa ao longo do tempo | Mais rápida após a implementação |
| Ambiguidade de execução | Maior, pois depende da interpretação humana | Menor, pois a execução é padronizada |
| Reuso | Limitado | Alto, quando o teste é bem projetado |
| Exploração de comportamentos inesperados | Forte | Fraca |
| Sensibilidade ao humor e ao cansaço | Alta | Baixa | 

A leitura correta dessa comparação não é “manual versus automático”, mas sim **manual e automático em colaboração**. O teste manual continua valioso na investigação; a automação se destaca na regressão, na repetição e na confiabilidade operacional [1].

### 1.2 O que costuma ser um bom candidato à automação

Este conteúdo enumera como bons candidatos à automação os **testes de regressão**, os **testes de fumaça**, funcionalidades críticas, cálculos matemáticos, formulários com múltiplas variáveis e tarefas repetitivas [1]. Há uma lógica clara por trás dessa seleção: são cenários em que a repetição é frequente, a combinação de entradas é significativa ou o impacto do defeito é alto.

Em contrapartida, nem tudo deve ser automatizado. Funcionalidades ainda muito novas, pouco utilizadas, instáveis, meramente visuais ou ainda em prototipação tendem a oferecer baixo retorno sobre o esforço de automação [1]. A decisão de automatizar, portanto, precisa considerar **estabilidade, criticidade, frequência de execução e custo de manutenção**.

## 2. Princípios de testes automatizados

A ideia da **pirâmide de automação**, associada a Mike Cohn, funciona como referência para pensar a distribuição de esforço entre níveis de teste [1]. A interpretação didática da pirâmide é que a base deve concentrar testes mais baratos, rápidos e numerosos, enquanto o topo reúne testes mais lentos, mais caros e mais sensíveis a mudanças de interface.

Essa leitura ajuda a entender por que a automação de interface, embora muito útil, **não deve ser o único tipo de automação existente em um projeto**. Quando toda a estratégia fica concentrada em testes de interface, cresce o risco de manutenção cara, baixa velocidade e retorno tardio sobre defeitos. Por isso, este conteúdo também discute testes unitários, de integração e funcionais dentro da pergunta: **quando automatizar e o quê automatizar?** [1].

### 2.1 Quando automatizar e o que automatizar

O raciocínio se divide em três níveis. Nos **testes unitários**, a automação deve ocorrer durante o desenvolvimento e recair sobre unidades de código. Nos **testes de integração**, o foco passa para o comportamento combinado de componentes, serviços ou camadas. Nos **testes de sistema ou funcionais**, a automação ocorre após a implementação dos cenários e da especificação dos casos de teste, voltando-se à verificação da realização do requisito funcional [1].

| Tipo de teste | Quando automatizar | O que automatizar |
| --- | --- | --- |
| Unitário | Durante o desenvolvimento | Unidades de código-fonte |
| Integração | Durante o desenvolvimento | Integração entre módulos, serviços e dependências |
| Sistema/funcional | Após definição dos cenários e casos de teste | Funcionalidades implementadas e seus fluxos de uso |

## 3. TDD e sua relação com qualidade

Este conteúdo também introduz **TDD (Test Driven Development)** como prática de apoio à qualidade do software. Este conteúdo o apresenta como uma técnica bastante associada ao Extreme Programming e popularizada por Kent Beck, na qual o desenvolvedor escreve primeiro um teste, observa a falha, implementa o mínimo para fazê-lo passar e, em seguida, refatora o código com segurança [1].

Esse trecho é importante porque reforça uma distinção pedagógica: **nem toda automação de testes é TDD, mas TDD é uma forma estruturada de incorporar testes ao próprio processo de desenvolvimento**. O valor didático dessa seção está em mostrar que teste não é atividade exclusivamente posterior ao desenvolvimento; ele pode orientar o design do software desde o início [1].

Este conteúdo destaca ainda benefícios como código mais simples, design mais evolutivo, menor acoplamento, maior coesão e mais confiança para refatorações [1]. Em um contexto de ensino de automação, essa seção funciona como ponte entre qualidade de produto e qualidade de código.

## 4. Técnicas de identificação e elaboração de testes de caixa-preta

Após consolidar os fundamentos, este conteúdo passa para as **técnicas de projeto de testes de caixa-preta**. O objetivo pedagógico é mostrar que automação não começa no código do teste, mas na **boa escolha e organização dos cenários**. Em outras palavras, antes de automatizar é preciso decidir **quais casos realmente representam o comportamento esperado do sistema** [1].

### 4.1 Classes de equivalência

Classes de equivalência são definidas como particionamentos disjuntos do domínio de entrada, formados por subconjuntos que compartilham uma propriedade comum [1]. O valor pedagógico dessa técnica está em evitar redundância: em vez de testar todos os valores possíveis, escolhe-se um representante de cada classe relevante.

No contexto da calculadora de descontos, essa técnica aparece de forma implícita na separação das faixas de quantidade. As classes principais são: **quantidade menor ou igual a zero**, **quantidade entre 1 e 99**, **quantidade entre 100 e 999** e **quantidade maior ou igual a 1000**, combinadas com os tipos de cliente **A**, **B** e **C** [1] [2].

### 4.2 Pares ortogonais

Pares ortogonais são descritos como uma técnica voltada a combinações relevantes entre valores significativos de variáveis do problema, especialmente útil quando há atributos categóricos [1]. A intenção é reduzir a explosão combinatória, preservando boa cobertura de interações sem exigir teste exaustivo de todas as combinações possíveis.

Embora essa técnica não seja a base principal do exercício da calculadora, ela contribui para a formação conceitual do aluno ao mostrar que diferentes contextos pedem estratégias diferentes de seleção de dados de teste [1].

### 4.3 Tabela de decisão

A **tabela de decisão** ocupa posição central na parte prática. Este conteúdo a apresenta como uma forma estruturada de analisar o comportamento do software sob várias condições, organizando entradas, ações e regras em colunas que futuramente se tornam casos de teste [1].

No exercício da calculadora, a tabela de decisão organiza duas dimensões principais: **tipo de cliente** e **faixa de quantidade**, resultando em doze casos de teste no slide 60 [1]. Essa escolha é didaticamente excelente, porque mostra ao aluno como transformar regras de negócio em cenários objetivos, rastreáveis e automatizáveis.

### 4.4 Método dos valores-limite

Muitos defeitos se concentram justamente nas fronteiras do domínio de entrada, motivo pelo qual o **método dos valores-limite** deve ser usado para selecionar dados próximos às extremidades das classes de equivalência [1]. Isso é especialmente relevante na calculadora, porque as fronteiras **0/1**, **99/100** e **999/1000** são pontos naturais de risco.

Vale interpretar os valores do slide 60 também à luz desse método. Embora a tabela de decisão organize faixas, a implementação prática dos testes pode — e pedagogicamente deveria — priorizar valores de fronteira, como **0**, **1**, **99**, **100**, **999** e **1000** [1] [2].

### 4.5 Testes baseados em caso de uso

Este conteúdo também revisa os testes baseados em caso de uso ou histórias de usuário. A ideia central é que o testador crie pelo menos um caso de teste para o fluxo principal e, adicionalmente, casos para fluxos alternativos e de exceção [1]. Essa abordagem se conecta diretamente ao requisito `UC001 - Calcular Desconto de Produto`, que descreve fluxo principal, alternativas por tipo de cliente e por faixa de quantidade, além da exceção de quantidade inválida [2].

## 5. Especificação de casos de teste e transição para automação

O caso de teste especificado manualmente continua sendo a base para a execução automatizada [1]. Isso é um ponto metodológico relevante: **automação não substitui a engenharia de teste; ela a operacionaliza**. Antes do script existir, é necessário haver clareza sobre objetivo, pré-condições, entradas, passos, resultados esperados e critérios de aprovação.

Essa transição fica explícita quando a apresentação pergunta se existe uma forma mais rápida de repetir testes de sistema. A resposta conduz aos **testes funcionais automatizados**, que transformam a execução repetitiva dos casos de teste em uma rotina programável e reaproveitável [1].

## 6. Testes funcionais automatizados e Playwright

A parte final apresenta testes funcionais automatizados como testes de sistema executados automaticamente sobre a interface do sistema, com foco na verificação das funcionalidades [1]. Este conteúdo cita várias ferramentas possíveis para aplicações web e escolhe **Playwright** como tecnologia principal [1].

A escolha é coerente com o cenário didático, pois o Playwright oferece recursos modernos para navegação, localização de elementos, auto-waiting, execução em navegadores atuais e escrita de testes em TypeScript/JavaScript [4] [5] [6]. Além disso, a própria documentação oficial destaca a centralidade dos **locators**, das **web-first assertions** e da organização do código de testes em estruturas mais sustentáveis, como o **Page Object Model** [4] [5] [6].

## 7. Aplicação prática: Calculadora de Descontos

O sistema utilizado como referência é a **Calculadora de Descontos**, disponibilizada publicamente pelo professor e associada ao requisito `UC001 - Calcular Desconto de Produto` [2] [3]. O fluxo observado na prática confirma a navegação descrita no requisito: o usuário acessa a página inicial, entra na listagem de produtos, seleciona o ícone `$` para um item, informa o tipo de cliente e a quantidade e aciona o cálculo [2] [3].

| Etapa funcional | Comportamento esperado no requisito | Comportamento observado no sistema |
| --- | --- | --- |
| Entrada na funcionalidade | Acesso à listagem de produtos e escolha do item para cálculo | Confirmado em `/produtos` [2] [3] |
| Dados do produto | Código, nome e valor preenchidos automaticamente | Confirmado no formulário [2] [3] |
| Informações complementares | Tipo de cliente e quantidade | Confirmado no formulário [2] [3] |
| Resultado | Exibir tipo, quantidade, fator de desconto e valor final | Confirmado na tela de resultado [2] [3] |
| Mensagem de sucesso | “Valor do desconto calculado com sucesso!” | Na interface observada, aparece “Fator de desconto calculado com sucesso!” [2] [3] |

Essa comparação já revela um ponto importante para ensino de testes: **nem sempre o sistema implementado coincide integralmente com o requisito especificado**. Esse tipo de divergência é extremamente útil, porque permite mostrar que testes automatizados servem justamente para tornar visíveis esses desalinhamentos.

## 8. Regras de negócio da calculadora

O requisito descreve as regras de desconto a partir da combinação entre **tipo de cliente** e **quantidade**. Para quantidades menores que 100 unidades, os fatores são `0,90`, `0,85` e `0,80` para clientes `A`, `B` e `C`, respectivamente. Para quantidades entre 100 e 999, os fatores passam a `0,95`, `0,90` e `0,85`. Para quantidades maiores ou iguais a 1000, os fatores tornam-se `1,00`, `0,95` e `0,90` [2].

| Faixa de quantidade | Cliente A | Cliente B | Cliente C |
| --- | --- | --- | --- |
| `1` a `99` | `0,90` | `0,85` | `0,80` |
| `100` a `999` | `0,95` | `0,90` | `0,85` |
| `1000` ou mais | `1,00` | `0,95` | `0,90` |

Além disso, o requisito estabelece que **quantidades menores ou iguais a zero** devem produzir a mensagem `A quantidade informada deve ser maior ou igual a 01 (um)!` [2]. Entretanto, a inspeção do sistema mostrou um comportamento divergente: ao menos no cenário executado com cliente `A` e quantidade `0`, a aplicação retornou uma tela de sucesso, calculando desconto normalmente em vez de sinalizar erro [3].

> Do ponto de vista pedagógico, essa discrepância é valiosa: ela permite ensinar que um teste bem automatizado não apenas confirma comportamentos corretos, mas também evidencia **defeitos de implementação** e **inconsistências entre especificação e sistema executável** [2] [3].

## 9. Os 12 casos de teste

A tabela de decisão consolidada organiza doze casos de teste a partir da combinação entre três tipos de cliente e quatro classes de quantidade. Os três primeiros casos correspondem ao fluxo de exceção. Os nove demais correspondem aos fluxos válidos de cálculo [1] [2].

| CT | Tipo de cliente | Quantidade | Resultado esperado principal |
| --- | --- | --- | --- |
| CT01 | A | `≤ 0` | Exibir `MSG002` |
| CT02 | B | `≤ 0` | Exibir `MSG002` |
| CT03 | C | `≤ 0` | Exibir `MSG002` |
| CT04 | A | `1 – 99` | Fator `0,90` e cálculo com sucesso |
| CT05 | B | `1 – 99` | Fator `0,85` e cálculo com sucesso |
| CT06 | C | `1 – 99` | Fator `0,80` e cálculo com sucesso |
| CT07 | A | `100 – 999` | Fator `0,95` e cálculo com sucesso |
| CT08 | B | `100 – 999` | Fator `0,90` e cálculo com sucesso |
| CT09 | C | `100 – 999` | Fator `0,85` e cálculo com sucesso |
| CT10 | A | `≥ 1000` | Fator `1,00` e cálculo com sucesso |
| CT11 | B | `≥ 1000` | Fator `0,95` e cálculo com sucesso |
| CT12 | C | `≥ 1000` | Fator `0,90` e cálculo com sucesso |

## 10. Elementos centrais do Playwright

Os slides finais concentram os recursos básicos usados para escrever testes funcionais com Playwright. O primeiro grupo é o de **locators**, com destaque para `getByRole`, `getByText`, `getByLabel`, `getByPlaceholder`, `getByAltText`, `getByTitle` e `getByTestId` [1] [5]. A documentação oficial enfatiza que locators são a peça central da ferramenta e sustentam a estratégia de auto-waiting e reavaliação do estado da página [5].

O segundo grupo reúne **ações e interações**, como `goto`, `click`, `fill`, `press`, `hover`, `check`, `uncheck`, `setInputFiles` e `selectOption` [1]. O terceiro grupo trata das **asserções**, como `toBeVisible`, `toContainText`, `toHaveAttribute`, `toHaveCount`, `toHaveText`, `toHaveValue`, `toHaveTitle` e `toHaveURL` [1] [6].

Por fim, este conteúdo revisita **hooks** (`beforeEach`, `afterEach`, `beforeAll`, `afterAll`) e o uso de **esperas configuradas** no `playwright.config.ts`, reforçando uma ideia correta e importante: **esperas fixas devem ser evitadas**, dando lugar a mecanismos mais declarativos e confiáveis de sincronização [1] [6].

## 11. Page Object Model como melhoria natural da solução

Embora o trecho de código apresentado na atividade original use diretamente chamadas ao objeto `page`, a evolução natural do exercício é aplicar o padrão **Page Object Model**. A documentação oficial do Playwright afirma que page objects representam partes da aplicação, criam uma API de mais alto nível para os testes e simplificam a manutenção ao concentrar seletores em um só lugar [4].

No caso da Calculadora de Descontos, essa divisão faz muito sentido. Há pelo menos três responsabilidades claramente separáveis: **navegar até a listagem de produtos**, **preencher o formulário de cálculo** e **validar a tela de resultado**. Ao encapsular essas responsabilidades em classes próprias, os testes deixam de repetir detalhes de interface e passam a expressar melhor a intenção do cenário testado [3] [4].

## 12. Atividade prática final

A seguir está a atividade proposta a partir da versão melhorada do código fornecido. O objetivo é que o estudante deixe de implementar apenas um caso isolado e passe a estruturar a suíte com **Page Object Model**, mantendo explicitamente os comentários do padrão **AAA (Arrange, Act, Assert)**.

### 12.1 Enunciado da atividade

Reescreva a automação do caso `CT04` utilizando **Page Object Model** no Playwright. Em seguida, evolua a solução para cobrir **todos os 12 casos de teste** do slide 60, mantendo o padrão AAA nos testes e centralizando locators e ações em classes de página.

A atividade deve considerar o requisito `UC001 - Calcular Desconto de Produto` como fonte principal para os resultados esperados. Ao final da implementação, analise criticamente os resultados dos testes, especialmente os casos de erro `CT01`, `CT02` e `CT03`, pois a aplicação observada apresenta indícios de divergência em relação ao requisito para a entrada `0` [2] [3].

### 12.2 Estrutura sugerida do projeto

| Arquivo | Responsabilidade |
| --- | --- |
| `pages/ProductListPage.ts` | Abrir a listagem e selecionar o produto para cálculo |
| `pages/DiscountFormPage.ts` | Preencher cliente e quantidade, além de submeter o formulário |
| `pages/DiscountResultPage.ts` | Validar mensagens e campos da tela de resultado |
| `tests/calcular-desconto.spec.ts` | Implementar os 12 cenários com comentários AAA |

### 12.3 Versão melhorada do código com Page Object Model

Abaixo está uma proposta de reescrita do caso originalmente enviado, já organizada com Page Object Model e preservando os comentários AAA.

```ts
// pages/ProductListPage.ts
import { Page } from '@playwright/test';

export class ProductListPage {
  constructor(private readonly page: Page) {}

  async goto() {
    await this.page.goto('https://calculadora.diegoquirino.net/');
    await this.page.getByRole('link', { name: 'Calcular Desconto' }).click();
  }

  async selecionarPrimeiroProdutoParaCalculo() {
    await this.page.getByRole('link', { name: '$' }).first().click();
  }
}
```

```ts
// pages/DiscountFormPage.ts
import { Page } from '@playwright/test';

export class DiscountFormPage {
  constructor(private readonly page: Page) {}

  async selecionarTipoDeCliente(tipoDeCliente: 'A' | 'B' | 'C') {
    await this.page.getByRole('combobox').selectOption(tipoDeCliente);
  }

  async informarQuantidade(quantidade: number) {
    await this.page.getByRole('textbox', { name: 'Quantidade:' }).fill(String(quantidade));
  }

  async calcularDesconto() {
    await this.page.getByRole('button', { name: 'Calcular Desconto!' }).click();
  }

  async preencherFormulario(tipoDeCliente: 'A' | 'B' | 'C', quantidade: number) {
    await this.selecionarTipoDeCliente(tipoDeCliente);
    await this.informarQuantidade(quantidade);
  }
}
```

```ts
// pages/DiscountResultPage.ts
import { expect, Page } from '@playwright/test';

export class DiscountResultPage {
  constructor(private readonly page: Page) {}

  async validarMensagemDeSucesso() {
    await expect(this.page.locator('section')).toContainText(/calculado com sucesso/i);
  }

  async validarFatorDeDesconto(fator: string) {
    await expect(this.page.getByRole('textbox', { name: 'Fator de desconto:' })).toHaveValue(new RegExp(fator));
  }

  async validarTipoDeCliente(tipoDeCliente: 'A' | 'B' | 'C') {
    await expect(this.page.getByRole('textbox', { name: 'Tipo de Cliente:' })).toHaveValue(tipoDeCliente);
  }

  async validarQuantidade(quantidade: number) {
    await expect(this.page.getByRole('textbox', { name: 'Quantidade orçada:' })).toHaveValue(String(quantidade));
  }

  async validarMensagemDeErro(mensagem: RegExp) {
    await expect(this.page.locator('section')).toContainText(mensagem);
  }
}
```

```ts
// tests/calcular-desconto.spec.ts
import { test } from '@playwright/test';
import { ProductListPage } from '../pages/ProductListPage';
import { DiscountFormPage } from '../pages/DiscountFormPage';
import { DiscountResultPage } from '../pages/DiscountResultPage';

test('CT04: Calcular Desconto - Cliente A, Quantidade 1-99', async ({ page }) => {
  const productListPage = new ProductListPage(page);
  const discountFormPage = new DiscountFormPage(page);
  const discountResultPage = new DiscountResultPage(page);

  // A - Arrange
  const quantidade = 99;
  const tipoDeCliente = 'A';

  await productListPage.goto();
  await productListPage.selecionarPrimeiroProdutoParaCalculo();

  // A - Act
  await discountFormPage.preencherFormulario(tipoDeCliente, quantidade);
  await discountFormPage.calcularDesconto();

  // A - Assert
  await discountResultPage.validarTipoDeCliente(tipoDeCliente);
  await discountResultPage.validarQuantidade(quantidade);
  await discountResultPage.validarFatorDeDesconto('0,90');
  await discountResultPage.validarMensagemDeSucesso();
});
```

### 12.4 Desafio: implementar os 12 casos a partir de massa de dados

***Após concluir a reescrita do `CT04`, implemente os demais cenários usando a tabela do item 9.***

### 12.5 Critérios de correção para a atividade

| Critério | Expectativa |
| --- | --- |
| Uso de POM | Os locators e ações devem estar encapsulados em classes de página |
| Padrão AAA | Cada teste deve manter explicitamente as seções Arrange, Act e Assert |
| Reuso | Os testes devem evitar repetições  |
| Cobertura | Os 12 casos do slide 60 devem ser implementados |
| Rastreabilidade | Cada caso deve manter identificação `CT01` a `CT12` |
| Qualidade das asserções | Deve haver verificação de fator, quantidade, tipo e mensagem conforme o cenário |
| Análise crítica | O aluno deve registrar qualquer divergência entre requisito e sistema |

### 12.6 Observação didática importante

Se os casos `CT01`, `CT02` e `CT03` falharem no ambiente real, isso **não significa necessariamente que o teste está errado**. Pode significar que o teste está corretamente apontando um defeito de implementação ou uma divergência entre requisito e sistema executável. Em contexto educacional, essa é uma oportunidade valiosa para discutir **oráculo de teste**, **rastreabilidade** e **triagem de defeitos** [2] [3].

## Conclusão

Este conteúdo de automação com Playwright articula, de maneira muito produtiva, três competências essenciais para a formação em testes de software. A primeira é a competência conceitual: entender por que automatizar e quando isso faz sentido. A segunda é a competência analítica: saber transformar regras e requisitos em casos de teste consistentes, usando técnicas como tabela de decisão, classes de equivalência e valores-limite. A terceira é a competência instrumental: implementar esses testes com uma ferramenta moderna, utilizando boas práticas de estruturação, asserções e manutenção [1] [2] [4] [5] [6].

Ao transformar o exemplo isolado em uma atividade baseada em **Page Object Model**, o exercício ganha mais aderência a práticas profissionais de automação. Ele deixa de ser apenas uma demonstração técnica e passa a funcionar como um pequeno laboratório de engenharia de testes, no qual requisitos, implementação, dados de teste e evidências de defeito se conectam de forma explícita.

## Referências

[1]: https://github.com/diegoquirino/facisa-gqs/blob/main/Oficina%20de%20Automa%C3%A7%C3%A3o%20de%20Testes%20com%20Playwright.pdf "Oficina de Automação de Testes com Playwright"
[2]: https://github.com/diegoquirino/facisa-gqs/blob/main/UC001%20-%20Calcular%20Desconto%20de%20Produto.claret "UC001 - Calcular Desconto de Produto"
[3]: https://calculadora.diegoquirino.net/ "Calculadora de Descontos"
[4]: https://playwright.dev/docs/pom "Page object models | Playwright"
[5]: https://playwright.dev/docs/locators "Locators | Playwright"
[6]: https://playwright.dev/docs/test-assertions "Assertions | Playwright"
