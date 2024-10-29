# Git Flow: Estrutura e Prática no Controle de Versão

Git Flow é um modelo de ramificação que facilita o gerenciamento de desenvolvimento de software ao organizar a criação e integração de branches de maneira estruturada. Criado por Vincent Driessen, esse modelo é especialmente útil para equipes colaborativas e projetos de médio a grande porte, ajudando a manter o controle sobre versões de produção e desenvolvimento simultâneo de novas funcionalidades.

## Por que Usar Git Flow?

Git Flow oferece um processo claro para gerenciar o ciclo de vida de desenvolvimento com uma estrutura que separa o código em produção do código em desenvolvimento. Isso evita que funcionalidades em progresso sejam incluídas acidentalmente em lançamentos de produção e facilita o gerenciamento de lançamentos, correções rápidas e novas funcionalidades em paralelo.

### Como o Git Flow Funciona?

O Git Flow introduz um conjunto de branches com papéis definidos, cada um usado em um contexto específico do desenvolvimento:

![alt text](image-1.png)
*Fonte: [Atlassian](https://www.atlassian.com/br/git/tutorials/comparing-workflows/gitflow-workflow)*

## Branches no Git Flow

O fluxo define dois tipos principais de branches:

1. **Branches principais**: Estão sempre presentes e representam o estado principal do projeto.
2. **Branches de suporte**: Criados conforme necessário, facilitam o desenvolvimento de novas funcionalidades, a criação de releases e a aplicação de correções rápidas.

### Branches Principais

- **master**: É o branch de produção, onde o código sempre deve estar estável e pronto para lançamento. Apenas commits de releases testadas e aprovadas são incorporados aqui.
- **develop**: Serve como base para o desenvolvimento da próxima versão. Todos os branches de novas funcionalidades são integrados aqui, e o código no branch `develop` sempre deve estar em um estado que funciona, embora possa não estar finalizado.

### Branches de Suporte

- **feature**: Criado a partir de `develop` para desenvolvimento de novas funcionalidades. Esse branch é removido assim que a funcionalidade é finalizada e integrada ao `develop`.
- **release**: Criado para preparar o código para uma nova versão de produção. Esse branch permite que a equipe faça ajustes finais, correções de bugs e testes antes de integrar o código ao `master`.
- **hotfix**: Criado diretamente a partir de `master` para aplicar correções urgentes em produção. Após resolver o problema, ele é integrado tanto ao `master` quanto ao `develop`, garantindo que a correção esteja presente em ambas as versões.

## Iniciando com Git Flow

Antes de usar o Git Flow, é importante já ter o repositório Git configurado. No entanto, você também pode iniciar um projeto com o Git Flow desde o início.

1. **Inicialize o Git Flow** no repositório:
   ```sh
   git flow init
	```
Esse comando configurará os branches `master` e `develop` automaticamente e pedirá confirmação para as convenções padrão de nomes dos branches de suporte.

2. **Crie uma nova feature:**
   ```sh
   git flow feature start <nome_da_feature>
	```
Isso cria um novo branch a partir de `develop`, onde você pode trabalhar na funcionalidade específica. Esse branch geralmente segue o nome da funcionalidade (por exemplo, `git flow feature start login` para a funcionalidade de login).

3. **Finalize a feature:**
   ```sh
   git flow feature finish <nome_da_feature>
	```
Ao finalizar a feature, ela é integrada ao branch `develop`, e o branch de funcionalidade é excluído. Isso mantém o repositório organizado e evita acúmulo de branches desnecessários.

# Publicando e Colaborando em uma Feature

Se você estiver em uma equipe e deseja compartilhar o progresso de uma `feature` antes de finalizá-la, use:

## 1. Publicar a feature:

   ```sh
   git flow feature publish <nome_da_feature>
```
Isso envia o `branch` para o repositório remoto, permitindo que outros desenvolvedores colaborem.

## 2. Baixar uma feature publicada por outro usuário:
   ```sh
   git flow feature pull origin <nome_da_feature>
```
Esse comando obtém o `branch` para que você possa colaborar e contribuir com a feature em questão.

# Lidando com Releases e Hotfixes

## 1. Criar um branch de release:
   ```sh
   git flow release start <versão>
```
O branch de release permite fazer ajustes finais e correções antes de lançar a versão. Depois de testado e aprovado, finalize-o com:
   ```sh
	git flow release finish <versão>
```

## 2. Criar e finalizar um hotfix:
   ```sh
	git flow hotfix start <nome_do_hotfix>
```
Após aplicar a correção necessária:
  ```sh
	git flow hotfix finish <nome_do_hotfix>
```

## Recursos e Sugestões para Aprendizado

Para quem deseja se aprofundar, seguem algumas sugestões de recursos:

- **Documentação do Git e Git Flow**  
  Consulte o [site oficial do Git](https://git-scm.com/doc) para entender os fundamentos e o [tutorial de Git Flow da Atlassian](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow) para aprender sobre o fluxo e ver exemplos de uso.

- **GUI para Git**  
  Ferramentas gráficas como o [SourceTree](https://www.sourcetreeapp.com/) (que possui Git Flow integrado) ou o [GitKraken](https://www.gitkraken.com/) ajudam a visualizar branches e facilitam o uso de comandos do Git Flow.

- **Prática com Projetos Reais ou Simulados**  
  Considere iniciar um projeto pessoal utilizando Git Flow ou participe de projetos em equipe no GitHub. A experiência prática com projetos reais ajuda a compreender a dinâmica dos branches e do fluxo de trabalho.

- **Curso Completo de Git**  
  Plataformas como [Udemy](https://www.udemy.com/), [Alura](https://www.alura.com.br/) e [Coursera](https://www.coursera.org/) oferecem cursos de Git que abordam conceitos fundamentais e práticas avançadas, incluindo o Git Flow.
