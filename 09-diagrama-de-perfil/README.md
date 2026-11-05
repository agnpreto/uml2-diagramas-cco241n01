# Diagrama de Perfil

**Grupo 9:** Yasmin e Rafaela

> Apague as instruções entre colchetes e preencha cada seção.

## Definição

O *Diagrama de Perfil* (Profile Diagram) é um diagrama estrutural da UML usado para *estender e personalizar a própria UML*. Em vez de modelar um sistema específico, ele permite criar um "dialeto" da UML para um domínio, plataforma ou tecnologia (por exemplo: web, banco de dados, sistemas bancários).

Ele faz isso por meio de três mecanismos:

- *Estereótipos:* novos tipos de elementos criados a partir de elementos que já existem na UML (ex.: «Entidade» criado a partir de Class).
- *Valores atribuídos (tagged values):* propriedades extras que o estereótipo carrega (ex.: tabela: String).
- *Restrições (constraints):* regras que limitam como o estereótipo pode ser usado (ex.: {o preço deve ser maior que 0}).

*Para que serve:* adaptar a UML a um contexto específico sem precisar alterar a linguagem original, deixando os modelos mais expressivos e padronizados para quem trabalha naquele domínio.

## Quando usar

- Quando a UML "pura" não é suficiente para representar conceitos de um *domínio específico* (saúde, finanças, jogos, etc.).
- Quando a equipe quer *padronizar a modelagem* de uma tecnologia ou framework (ex.: classes que são entidades de banco, controladores, serviços).
- Na fase de *arquitetura e projeto*, antes ou junto da criação dos diagramas de classes e componentes, para definir o vocabulário que será usado nos demais diagramas.
- Quando ferramentas de modelagem ou geração de código precisam reconhecer elementos customizados.

Em projetos pequenos ele quase não é necessário, e é mais útil em projetos grandes ou em organizações que padronizam seus modelos.

## Elementos da notação

| Símbolo | Nome | O que representa |
|---|---|---|
| Pacote com a palavra-chave «profile» | *Perfil (Profile)* | O pacote que agrupa todos os estereótipos e regras da extensão. É o "contêiner" da personalização. |
| Retângulo de classe com «metaclass» | *Metaclasse* | Um elemento já existente da UML (ex.: Class, Component, Actor) que será estendido. |
| Retângulo de classe com «stereotype» | *Estereótipo* | O novo elemento criado a partir de uma metaclasse. Pode ter atributos (tagged values). |
| Seta contínua com *ponta triangular preenchida (preta), do estereótipo para a metaclasse | **Extensão (Extension)* | Indica qual metaclasse o estereótipo estende. |
| Atributos dentro do estereótipo (ex.: tabela: String) | *Valor atribuído (Tagged value)* | Propriedade adicional que o estereótipo passa a ter. |
| Texto entre chaves { ... } | *Restrição (Constraint)* | Regra que o elemento deve obedecer (pode ser escrita em OCL ou em texto livre). |
| Retângulo com «enumeration» | *Enumeração* | Lista fixa de valores que um atributo do estereótipo pode assumir. |
| Seta tracejada com «apply» | *Aplicação de perfil (Profile Application)* | Indica que um modelo ou pacote está usando aquele perfil. |
| Seta tracejada com «reference» | *Referência ao metamodelo* | Indica que o perfil se baseia no metamodelo da UML. |
| Nome entre aspas angulares, ex.: «Entidade» | *Notação de estereótipo* | Forma de mostrar, em outros diagramas, que um elemento usa um estereótipo. |


## Exemplo prático

*Sistema escolhido:* uma *Loja Virtual*.

O perfil se chama LojaVirtualProfile e cria vocabulário próprio para esse tipo de sistema:

- *«Entidade»* estende a metaclasse Class e representa classes que viram tabelas no banco de dados. Tem o valor atribuído tabela: String.
- *«Controlador»* estende a metaclasse Class e representa classes que recebem requisições do usuário. Tem o valor atribuído rota: String.
- *«ServicoExterno»* estende a metaclasse Component e representa integrações com sistemas de fora, como o gateway de pagamento. Tem o valor atribuído url: String.

O diagrama mostra o pacote «profile» LojaVirtualProfile com esses três estereótipos ligados às suas metaclasses por setas de extensão. Depois, em um diagrama de classes da loja, podemos escrever «Entidade» Produto ou «Controlador» PedidoController, e quem lê entende o papel de cada classe sem precisar de explicação extra.

## Comparação com Caso de Uso, Classe e Sequência

| Diagrama | O que modela | Semelhança com o de Perfil | Diferença principal |
|---|---|---|---|
| *Caso de Uso* | As funcionalidades do sistema do ponto de vista dos atores | Ambos são diagramas UML e podem usar estereótipos (ex.: «include», «extend») | O Caso de Uso descreve *o que o sistema faz. O de Perfil não descreve o sistema, e sim **como personalizar a linguagem* usada para modelá-lo. |
| *Classe* | A estrutura estática: classes, atributos, métodos e relacionamentos | A notação é bem parecida (retângulos com atributos, setas), e o estereótipo é desenhado como uma classe | A Classe modela *os objetos do sistema. O de Perfil modela **os tipos de elementos* que podem ser usados nos diagramas (está um nível acima, no metamodelo). |
| *Sequência* | A troca de mensagens entre objetos ao longo do tempo | Ambos fazem parte da UML e podem exibir elementos com estereótipos | A Sequência é *comportamental* e mostra a ordem das interações. O de Perfil é *estrutural* e não tem noção de tempo nem de fluxo. |

*Resumindo:* os diagramas de Caso de Uso, Classe e Sequência modelam o sistema. O Diagrama de Perfil modela a própria linguagem de modelagem, e é por isso que costuma ser o menos usado no dia a dia, mas o mais flexível.


## Apresentação

[Apresentação (PDF)](apresentacao.pdf) — o exemplo prático está no slide 5 e 6 .

## Referências

- OBJECT MANAGEMENT GROUP (OMG). *Unified Modeling Language (UML) Specification, versão 2.5.1.* Disponível em: https://www.omg.org/spec/UML/2.5.1
- BOOCH, G.; RUMBAUGH, J.; JACOBSON, I. *UML: Guia do Usuário.* 2. ed. Rio de Janeiro: Elsevier, 2006.
- FOWLER, M. *UML Essencial: um breve guia para a linguagem-padrão de modelagem de objetos.* 3. ed. Porto Alegre: Bookman, 2005.
- VISUAL PARADIGM. *UML Profile Diagram Tutorial.* (consultar no site da Visual Paradigm).
