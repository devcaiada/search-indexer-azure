# Azure Cognitive Search

Vamos criar um indexador de pesquisa junto ao serviço de IA de pesquisa da Azure Microsoft.

## Criar recurso do Asure AI Search

No [Portal Azure](https://portal.azure.com/), clique [+Criar recurso], na aba à esquerda, selecione em categoria [AI + Machine Leraning], depois clique em [AI Search] como na imagem abaixo.

![01](https://uploaddeimagens.com.br/images/004/741/496/original/01.jpg?1708112910)

Na sequência, dentro de AI Search, clique em criar e preencha os campos da seguinte forma:

**Subscription**: Sua inscrição Azure

**Resource group**: Selecione seu resource group

**Service name**: Crie um nome único para o serviço

**Location**: West US 2

**Pricing tier**: Basic

![02](https://uploaddeimagens.com.br/images/004/741/508/original/02.jpg?1708113486)

Após isso clique em [Review + Create] e depois em [Create].

## Criar o Storage

Para seguirmos será necessário criar um _storage_, que é como um cofre para podermos armazenar alguns dados.

Na página de Serviços do Azure clique em Storage accounts e depois em Create para abrirmos um serviço de Storage.

![03](https://uploaddeimagens.com.br/images/004/742/920/original/03.jpg?1708367247)

Ao abrir a página de criação do Storage, configure-o da seguinte forma:

- **Subscription**: Selecione sua inscrição do Azure
- **Resource group**: Selecione o seu grupo de trabalho criado anteriormente
- **Storage account name**: Crie um nome único para o serviço
- **Region**: Dê preferencia para West US por ser mais barato o serviço
- **Performance**: Standard
- **Redundancy**: selecione LRS

![04](https://uploaddeimagens.com.br/images/004/742/936/original/04.jpg?1708367699)

Após a configuração clique em Review e depois em Create.

### Permitindo acesso anônimo ao Blob

Para podermos prosseguir nosso estudo, é necessário que após criar o Storage, entrar em configurações do mesmo e permitir acesso anônimo ao Blob para facilitar nossas implementações.

![05](https://uploaddeimagens.com.br/images/004/742/948/original/05.jpg?1708368009)

### Criando o Container

Ainda dentro do Storage que vc acabou de criar, na aba esquerda procure por Containers e depois clique em + Container para criar um novo.

![06](https://uploaddeimagens.com.br/images/004/742/962/original/06.jpg?1708368960)

Preencha o nome e o Anonymous acess level conforme a documentação e por final clieque em Create.

### Upload dos reviews

Acesse o container que acabou de criar com o nome de acordo com a documentação, clique em + Upload e selecione os arquivos conforme documentação Azure.

![07](https://uploaddeimagens.com.br/images/004/742/986/original/07.jpg?1708369976)

## Ai SEARCH: Importação e indexação de dados

Agora que já criamos tudo que necessitávamos, vamos linkar os dados que subimos para o Container com o serviço AI Search da Azure.

Para isso vamos voltar a abrir o serviço AI Search que criamos e na aba superior clicar em

![08](https://uploaddeimagens.com.br/images/004/743/009/original/08.jpg?1708370732)

Na página que abrir, selecione o tipo Azure Blob Storage e configure a conexão conforme imagem abaixo. Atente-se apenas para o campo Connection string, onde você deve clicar em Choosing an existing connection e selecionar o container que acabamos de criar.

![09](https://uploaddeimagens.com.br/images/004/743/029/original/09.jpg?1708372012)

Continuando clique em Review and Create.

Para configurarmos nossos indexadores desejados é imprescindível seguir a [documentação](https://microsoftlearning.github.io/mslearn-ai-fundamentals/Instructions/Labs/11-ai-search.html) sem nenhum erro.

Na parte Index the documents, siga as especificações 05 até a 17 para podermos continuar. Aqui você irá criar seus indexadores para analisar as reviews que fizemos o upload anteriormente.

## Consultando o índice criado

Após linkarmos os dados a serem analisados e os nossos indexadores, vamos consultá-los. Abra novamente o serviço AI Search e agora clique em Search Explorer.

![10](https://uploaddeimagens.com.br/images/004/743/032/original/10.jpg?1708372426)

Dentro de Search Explorer, em Index selecione o nome do index que criou anteriormente. Logo abaixo no campo Search podemos utilizar alguns comando para ver alguns resultados.

![11](https://uploaddeimagens.com.br/images/004/743/034/original/11.jpg?1708372723)

Aqui vão alguns comandos que você pode utilizar em seus testes:

- **search=\*&$count=true** (Consulta o funcionamento da aplicação.)
- **search=locations:'Chicago'** (Consulta as ocorrências acontecidas em Chicado.)
- **search=sentiment:'negative'** (Consulta as ocorrências com sentimento negativo.)

## Conclusão

Com AI Search da Azure podemos ter uma pequena noção da eficiência e potência das ferramentas de IA. Podemos consultar uma grande quantidade de documentos, extraindo as principais informações, realizar pesquisas avançadas e até mesmo analisar reviews de produtos e serviços, indentificando os sentimentos principais dos mesmos.
