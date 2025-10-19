## 1. Introducao
Esta documentação tem como objetivo ser um guia de referencia para a padronização dos artefatos e diretivas utizadas no processo de desenvolvimento de *software*. Este guia abrange tantos os processo propriamente dito, como os artefatos inerentes ao *software*. Dentre os artefatos estão: a arquitetura, a codificacao, a acessibilidade, a seguranca, os testes e as operacoes envolvidas no desenvolvimento do *software*.


## 2. Arquitetura e Design
Quanto a arquitetura e *design*, as seguintes recomendações devem ser observadas:

- *Execução*: microservicos, *serverless* ou monolitico modular.
- *Design Patterns*: *factory*, *singleton*, *repository*, *service layer* e *strategy*.
- *Arquitetura Recomendada*: Clean Architecture e DDD.
- *Diagramas*: componentes, sequencia, classe e infraestrutura.


### 2.1.1 Clean Archicture
Clean Architecture é um modelo de arquitetura de *software*e proposto por Robert C. Martin (Uncle Bob), que tem como objetivo criar sistemas organizados, robustos, independentes de frameworks, e de fácil manutenção, evolução e teste.


### 2.1.3 Domain-Driven Designe
O Domain-Driven Design (DDD), ou Design Orientado ao Domínio, é uma abordagem de desenvolvimento de *software* proposta por Eric Evans que tem como objetivo centralizar o desenvolvimento no modelo de negócio, alinhando o *software* às regras e processos da organização. Essa abordagem prioriza a modelagem centrada no domínio, onde as entidades, objetos de valor, agregados, repositórios e serviços são estruturados de acordo com a lógica e os conceitos do negócio. Um dos pilares do DDD é a Linguagem Ubíqua, que estabelece uma linguagem comum entre desenvolvedores e especialistas do negócio, garantindo entendimento compartilhado e eliminando ambiguidades. Além disso, DDD introduz o conceito de Bounded Context (Contexto Delimitado), que permite isolar modelos, regras e linguagens específicas dentro de cada contexto de negócio, facilitando a comunicação entre diferentes partes do sistema por meio de APIs, eventos ou contratos bem definidos. A aplicação de DDD promove a clareza no desenvolvimento de sistemas complexos, facilita a manutenção, aumenta a consistência e assegura que o software reflita fielmente as regras e necessidades do domínio empresarial.


### 2.1.4 Design Pattern
Utilize as seguintes definições para cada Design Pattern:

- *Factory*: padrão que encapsula a criação de objetos, centralizando a logica de instancia para garantir consistencia e flexibilidade.
- *Singleton*: garante que uma classe possua apenas uma instancia em todo o sistema, proporcionando um ponto de acesso global.
- *Repository*: atua como uma camada intermediaria entre o dominio e a persistencia, abstraindo o acesso a dados e operacoes no banco.
- *Service Layer*: organiza a logica de negócio em servicos, separando-a dos detalhes de controle, apresentação ou infraestrutura.
- *Strategy*: permite definir uma familia de algoritmos, encapsula-los e torna-los intercambiaveis em tempo de execucao, promovendo flexibilidade no comportamento.


## 3. Padrões de Codificação
Os padrões de referencias de codificação a serem utilizados durante a implementação e condução do processo de desenvolvimento são:

- *Linguagem de Referencia*: utilizar o Python 3.10
- *Convenção*: seguir PEP 8 e PEP 257.
- *Linhas*: para linhas de código e de comentários use até 80 colunas.
- *Indentacao*: utilize 4 (quatro) espaços, não utilizar TABs.

### 3.1 Estrutura do Projeto
Utilize como referencia a organização abaixo:

```plaintext
meu_projeto/
├── src/
│   ├── core/
│   ├── services/
│   ├── models/
│   ├── main.py
├── tests/
├── docs/
├── requirements.txt
├── README.md
```

- *meu_projeto/*: pasta raiz do projeto, contem todo o codigo e arquivos relacionados.
- *src/*: pasta que armazena o código-fonte do *software*.
- *core/*: módulo com funcionalidades essenciais e transversais, como *logs*, exceções, configurações e utilitários.
- *services/*: contém as regras de negocio e servicos da aplicação.
- *models/*: modelos de dados, entidades e objetos de dominio (DDD).
- *main.py*: arquivo principal para inicialização e execução da aplicação.
- *tests/*: diretório que contém todos os testes unitários, integração e E2E.
- *docs/*: documentacao técnica, diagramas, manuais e de referência do projeto.
- *requirements.txt*: lista de dependencias (bibliotecas de módulos e as respectivas versões) necessárias para o projeto.
- *README.md*: documento de apresentação do projeto, instruções de uso e contribuição.

> End-to-End (E2E) é um tipo de teste que valida se o sistema como um todo funciona conforme esperado, simulando o comportamento do usuário ou o fluxo completo de uma aplicação do início ao fim.


### 3.2 Nomenclaturas
Referente as nomenclaturas que devem ser utilizadas nos elementos do código as seguintes referencias devem ser utilizadas para identificar:

- Funções e métodos: deve ser utilizado *snake_case*.
- Classes: deve ser utilizado PascalCase.
- Constantes: deve ser utilizado UPPER_CASE.
- Atributos: deve ser utilizado camelCase.


### 3.3 Depedências 
Insira as  dependencias no arqvivo requirements.txt e instale-as utilizando o pip:

```
## Em um ambiente Linux:
$ pip install -r requirements.txt
```

### 3.4 Diretrizes de Commit
Para *commits* considere:

- Use o padrão semântico de commits (feat:, fix:, chore:, docs:, test: etc.).
- Inclua o identificador da issue correspondente, se houver (ex: feat(api): add user endpoint #123).
- Cada *commit* deve ser autocontido e reversível.


### 3.5 Pull Requests
Cada *pull request* deve conter:

- Um resumo objetivo das alterações.
- Prints, logs ou exemplos de execução (quando aplicável).
- Plano de teste, incluindo comandos executados localmente.
- Notas sobre migrações, variáveis de ambiente ou dependências alteradas.
- O PR deve ser revisado por outro mantenedor Python e passar por todos os estágios de CI antes do merge.
- Prefira rebase em vez de merge para manter histórico linear.


### Notas de Ambiente
Sobre o ambiente:

- Variáveis sensíveis devem residir em .env.local e nunca ser commitadas.
- Documente todas as novas variáveis no arquivo docs/configuration.md, incluindo valores padrão e finalidade.
- Caso o projeto utilize Docker, mantenha o Dockerfile.dev para ambiente local e valide se o contêiner inicia com docker compose up dev.


## 5. Segurança
A segurança é um aspecto fundamental no desenvolvimento de *software*. Neglegenciar este aspecto pode comprometer a itegridade do *software* e inviabilizar sua reparação posterior. Dentre as referencias utilizadas neste guis, recomenda-se:

- Seguir OWASP Top 10.
- Aplicar criptografia, mascaramento, *hashing* para dados sensiveis (base64 com *salt* utilizado frase de acesso). 
- Realizar a validação de entrada.
- Evitar dados sensíveis nos registros de logs.

> O OWASP Top 10 é uma lista criada pela organização Open Web Application Security Project (OWASP) que apresenta as 10 principais vulnerabilidades de segurança em aplicações (principalmente WEB).


## 6. Logs e Exceptions
É recomendado o uso da lib logging do Python, sendo o padrão de log que deve ser aplicado no código é como descrito abaixo:

```plaintext
[YYYY-MM-DD HH:MM:SS] [LEVEL] [NOME_MODULO]: mensagem
```
> O LEVEL será um dos seguintes elementos: INFO, DEBUG, ERROR, WARNING, CRITICAL.

Somado a isto é proposto o uso de *Exceptions* customizadas: ErroNegocio e ErroTecnico.


## 7. Testes
O desenvolvimento deve ser orientado à testes, sendo que a cada implementação de uma atividade (TASK), pelo menos um teste unitário deve ser produzido para validar aquela implementação. O *framework* de referencia indicado neste guia é o "pytest". Dos requisitos indicados estão:

- Cobertura minima: 80%.
- Tipos: unitários, integração e E2E.
- Validação: deve ser realizado por meio de esteiras CI/CD.
- Priorize testes de comportamento e lógica de decisão.
- Use pytest-mock ou unittest.mock para simular dependências.
- Para testes de integração, use pytest-asyncio se o projeto for assíncrono e pytest-docker para dependências externas (como banco de dados, mensageria etc.).
- Snapshot tests são aceitos apenas para validação de estruturas fixas (p.ex. schemas de resposta).
- O pipeline de CI deve bloquear merge caso pytest --cov falhe.


Os testes devem utilizar pytest, com estrutura mínima:

```plaintext
tests/
  ├── unit/
  │   ├── test_<module>.py
  ├── integration/
  │   ├── test_<feature>.py
```


## 9. Documentacao
- Docstrings conforme PEP 257.
- Ferramentas: Sphinx, MkDocs.
- APIs documentadas via OpenAPI/Swagger.


## 10. Checklist de Qualidade
A tabela abaixo possui um conjunto de requisitos que devem ser assumidos para validação de cada entrega (Task).

|ITEM | STATUS |
|---  |---     |
|Codigo segue PEP 8	        ||
|Testes > 80% cobertura	    ||
|Acessibilidade validada	  ||
|Sem dados sensiveis em log	||
|Documentacao atualizada	  ||
|Revisao de codigo feita    ||


## 11. Ferramentas e Bibliotecas
Como referência de ferramentas e biblioteca, use:

- *Backend*: Python (Flask, FastAPI, Django)
- *Frontend*: React, Angular, Vue
- *Logs*: Logging, ELK, Grafana
- *Testes*: Pytest, Cypress
- *CI/CD*: GitHub Actions, GitLab CI
- *Seguranca*: SonarQube, Dependabot, Bandit


## 12. Anexos
Esta seção apresenta os modelos de referencias para a criação e condução de projetos (estrutura de um projeto), da condiicação (conteúdo de um arquivo Python), e para criação de fluxogramas e diagramas.



### 12.3 Estrutura Python
Pra codificação, a seguinte estrutura deve ser assumida:


```plaintext
#!/usr/bin/env python3


###############################################################################
## IMPORT                                                                    ##
###############################################################################
## MANDATORY SECTION.
## In this section, imports of external modules to be used throughout the code
## should be included.
CONTENT

###############################################################################
## DEFINITION                                                                ##
###############################################################################
## OPTIONAL SECTION.
## In this section, the constants to be used throughout the code should be
## defined. Constants must be named in uppercase letters. Additionally,
## environment variables and configurations defined in external files are
## loaded in this section.
CONTENT

###############################################################################
## INITIALIZATIONS                                                           ##
###############################################################################
## OPTIONAL SECTION.
## In this section, initialization of external modules used in the code should
## be performed, as well as configurations such as suppressing warnings, for
## example.
CONTENT

###############################################################################
## METHODS                                                                   ##
###############################################################################
## OPTIONAL SECTION
## In this section, methods that are not associated with classes are coded.
## Often, methods are created as utilities for specific tasks and are not
## incorporated into a class.
CONTENT

###############################################################################
## CLASSES                                                                  ##
###############################################################################
CONTENT

###############################################################################
## MAIN                                                                      ##
###############################################################################
## MANDATORY SECTION.
## Many times it is necessary to execute the script directly. This block
## indicates to the interpreter that the script was invoked from the command
## line. It should be present to allow the functionality to be tested via the
## command line and to provide a certain degree of independence from other
## modules. This behavior is intended to ensure low coupling between modules.
if __name__ == "__main__":
    [CONTENT]
## EOF
```


### 12.4 Methods
Para implementação de métodos, use a seguinte estrutura:

```plaintext
##
def method_name(PARAMETERS):
    """"
    COMMENT
    """

    CODE
## END OF METHOD.
```


### 12.5 ,Classe
Para implementação de classes, use a seguinte estrutura:

```plaintext
##
class:
  
    """
    COMMENT
    """

    ## --------------------------------------------------------------------- ##
    ## ATTRIBUTES                                                            ##
    ## --------------------------------------------------------------------- ##
    ATTRIBUTES


    ## --------------------------------------------------------------------- ##
    ## SPECIAL METHODS                                                       ##
    ## --------------------------------------------------------------------- ##
    def __init__(self, PARAMETERS):
        CODE


    ## --------------------------------------------------------------------- ##
    ## PUBLIC METHODS                                                        ##
    ## --------------------------------------------------------------------- ##
    def nome_do_método_público_1(self, PARAMETERS):
        CODE

    def nome_do_método_público_N(self, PARAMETERS):
        CODE


    ## --------------------------------------------------------------------- ##
    ## PRIVATE METHODS                                                       ##
    ## --------------------------------------------------------------------- ##
    def __nome_do_método_privado_1(self, PARAMETERS):
        CODE

    def __nome_do_método_privado_2(self, PARAMETERS):
        CODE
## END OF METHOD.
```

