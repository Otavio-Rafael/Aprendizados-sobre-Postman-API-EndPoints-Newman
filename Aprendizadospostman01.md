## Primeiro crie um cadastro/conta no Potsman 
### Siga os passos abaixo

1. Acesse o site postman;
2. Clique em "Sign up for free" na parte esquerda e siga as instruções para criar sua conta;
3. Preencha os dados e finalize a criação da conta.
---

## Entendendo o PostMan, APIs e Endpoints e NewMan
### Será abordado somente o que foi explorado até o momento

#### WorkSpaces
1. Uma WorkSpace(chamdo de WS nesse documento) é ambiente que o Postman cria para que você possa realizar as suas atividades fornecendo alguns recursos, no entanto só será abordado a parte de Collection.

#### Collections
1. Falando sobre as collections elá servirá para que você possa criar, editar, adicionar, testar e executar as suas APIs, podendo separar diversos projetos em collections diferentes;
2. Após criar uma collection dentro dela você pode criar pastas e subpastas para organizar melhor suas APIs e Endpoints a sua maneira.

#### Request
1. Uma request (ou requisição) no Postman é o pedido que você envia para uma API;
2. Ela contém todas as informações necessárias para chamar um endpoint e obter uma resposta do servidor

    | Componente       | O que faz                                                                 |
    |------------------|---------------------------------------------------------------------------|
    | **Method (método)** | Define a **ação** que você quer realizar: `GET`, `POST`, `PUT`, `DELETE`, etc. |
    | **URL**          | O **endereço do endpoint da API** que você quer acessar.                 |
    | **Headers**      | Informações adicionais, como `Authorization`, `Content-Type`, etc.       |
    | **Body**         | Os **dados que você envia** (usado em métodos como `POST` e `PUT`).      |
    | **Params**       | Parâmetros que vão na URL (`?chave=valor`).                              |
    | **Auth**         | Onde você configura tokens, chaves de API ou autenticação básica.        |

3. Exemplo prático: Suponha que você quer cadastrar um novo produto em uma loja via API;
    1. Method: POST;
    2. URL: https://serverest.dev/Produtos;
    3. Headers;
        - Content-Type: application/json.
    4. Body;
        - {
            "nome": "Tênis",
            "preco": 199.90,
            "estoque": 15
            }


#### APIs
1. API significa Application Programming Interface (Interface de Programação de Aplicações);
2. Ela funciona como uma ponte que permite que diferentes sistemas, aplicações ou serviços se comuniquem entre si, é como um garçom em um restaurante;
    1. Você (cliente) faz um pedido (requisição);
    2. O garçom (API) leva o pedido até a cozinha (servidor);
    3. A cozinha prepara e devolve o prato (resposta) por meio do garçom.

#### EndPoints
1. Endpoints são os endereços específicos dentro de uma API que representam funcionalidades ou recursos.
Cada endpoint corresponde a uma ação possível que pode ser feita por meio da API;
2. Suponha uma API de uma loja virtual;

| Recurso  | Endpoint                | Ação                         |
|----------|-------------------------|------------------------------|
| Produtos | `GET /produtos`         | Listar produtos              |
| Produto  | `GET /produtos/123`     | Detalhar um produto específico |
| Carrinho | `POST /carrinho`        | Adicionar item no carrinho  |
| Pedido   | `DELETE /pedido/456`    | Cancelar um pedido           |

#### NewMan
1. O Newman é a ferramenta de linha de comando do Postman que permite executar todas as requisições de uma collection de forma automatizada.
2. Ele é ideal para testes em pipeline ou localmente, sem abrir o Postman.
3. Ao final da execução, o Newman gera relatórios detalhados com o status de cada requisição.
---

## Criando uma collection
### Como criar uma collection

0. Após o login você já será direcionado para uma WS, mas pode criar outras caso prefira ou ache necessário
1. No canto superior esquerdo dentro da WS já estará aberto um menu lateral para que você crie a sua primeira collection, clique no "sinal de mais" no canto esquerdo superior ;
2. Ira abrir um novo menu;
3. Nesse novo menu selecione a opção "Blank collection" e você já tera uma nova collection para poder realizar seus testes;
---

## Criando e adicionando APIs e EndPoints a sua collection
### Siga os passos abaixo(O exemplo usado foi o de cadastrar um produto por ser o mais completo e com mais informações)

0. Primeiro entra na collection desejada e escolha a pasta que deseja caso tenha mais de uma;
1. Ao lado do nome da "Collection" ou "Pasta" Selecionada tem um sinal de "mais", ao clicar nele você vai criar uma request, que é onde você adiciona a API e EndPoint para os testes;
2. Após criar uma nova request no Postman, é exibida uma tela onde é possível inserir a URL da API, selecionar o método HTTP (GET, POST, etc.) e configurar parâmetros como Headers, Body, Authorization e Params. No botão Send, a requisição é enviada para o endpoint. Essa interface permite montar, testar e visualizar a resposta da API de forma detalhada;
    1. Parte superior – Montagem da requisição;

        - **URL**: Campo onde você insere o endereço do endpoint da API;
        - **Método HTTP**: Menu suspenso onde você escolhe a ação que quer executar (`GET`, `POST`, `PUT`, `DELETE`, etc);
        - **Botão Send**: Envia a requisição montada para o servidor da API e aguarda a resposta;
        - **Save**: Permite salvar a requisição dentro de uma collection.

    2. Parte intermediária – Configuração da requisição;

        - **Params**: Adiciona parâmetros de consulta (query strings) à URL, como `?chave=valor`;
        - **Authorization**: Define o tipo de autenticação usado na API (ex: Bearer Token, Basic Auth, etc);
        - **Headers**: Define cabeçalhos da requisição, como `Content-Type`, `Authorization`, etc;
        - **Body**: Permite enviar dados no corpo da requisição (usado em `POST`, `PUT`...), geralmente em JSON;
        - **Pre-request Script**: Scripts que rodam **antes** da requisição ser enviada;
        - **Tests**: Scripts de teste que rodam **depois** que a resposta da API é recebida;
        - **Settings**: Configurações específicas da requisição, como redirecionamento, timeout, etc.

    3. Parte inferior – Resposta da API.

        - Exibe o **status da resposta** (ex: 200 OK, 404 Not Found);
        - Mostra o **tempo de resposta**, o **tamanho do payload** e o **body da resposta**, geralmente em JSON;
        - Permite visualizar os **headers da resposta**, cookies, e também testar scripts se configurados.

3. Agora que a request já foi criada selecione o EndPoint desejado, nesse caso será usado o `Post`;
4. Pegue a URL da API `https://serverest.dev/Produtos` essa é a URL da API gratuita usada (**Vale ressaltar que a URL original com todos os endereçoes esta no final do documento essa URL terminando em `/produto`serve apenas para acessar os EndPoints de Produto, caso queira acessar os EndPoint de usuário troque o final por `/usuario`**);
5. Montando a request para cadastrar um novo produto. Para testar o endpoint de cadastro de produto (`POST https://serverest.dev/produtos`), foi necessário configurar alguns campos na requisição para garantir que a API aceite os dados e retorne a resposta esperada;
    1. Headers utilizados;

        - **Key: Authorization** Esse campo é obrigatório porque apenas usuários autenticados como **administradores** podem cadastrar novos produtos;
                - **Value:** 
                Para isso, você precisa estar logado com um usuário admin e copiar o **token** gerado no login (`POST /login`).  
                O valor deve ser passado no formato:  
                ```
                Bearer {seu_token}
                ```

        - **KEY: Content-Type**: Indica para a API o **tipo de dado** que está sendo enviado no corpo da requisição (Body);
                - **Value**
                Como os dados do produto estão em **JSON**, o valor desse header precisa ser:
                ```
                application/json
                ```

        - **KEY: Accept** (opcional): Informa o tipo de resposta que o cliente espera da API.
                - **Value**
                ```
                application/json
                ```

    2. Body da requisição.
        - **BODY: Composição** No corpo da requisição, foram enviados os dados do novo produto no formato JSON, como no exemplo abaixo:

                ```json
                {
                "nome": "vazo roxo",
                "preco": 40,
                "descricao": "vidro temperado",
                "quantidade": 15
                }
                ```

                - **nome**: nome do produto.
                - **preco**: valor numérico do produto.
                - **descricao**: descrição opcional ou detalhada do item.
                - **quantidade**: número de unidades a serem cadastradas.

                !!Importante!!: certifique-se de que o tipo selecionado em `Body` seja **raw** e o formato seja **JSON**. Isso é essencial para que a API interprete corretamente os dados enviados.

                ---

                Essa configuração completa permite que o Postman envie a requisição com sucesso e a API retorne a resposta correspondente ao cadastro do produto.

6. Após fazer toda a configuração bastar clicar em **SEND** ao lado da URL;
7. O resultado esperado deverá ser esse.
    - **Descrição**: 
        1. O Código informando qual foi o resultado, nesse caso se devera aparecer o código **201 created**;
            ```
            201 created
            ```
        2. Ao lado do código o tempo de retorno (se for a primeira vez usando vai demorar um pouco é normal);
            ```
            257ms
            ```
        3. Em **JSON** deverá apresentar uma mensagem descrevendo o que ocorreu e o ID do produto caso tenha sido cadastrado.
            ```
            {
                "message": "Cadastro realizado com sucesso",
                "_id": "aFbRVaJOG3yGhGfA"
            }
            ````
---

## Exportando uma collection para automatizar com o NewMan
### sia os passos para exportar(baixar) uma collection

1. clique nas no botão "três bolinhas" ao lado do nome da collection;
2. No menu que aparecer va em "More" no final;
3. No próximo menu clique em "Export" também no final;
4. Novamente no próximo menu selecione "collection2.1" para exportar a versão mais atualizada;
5. Após escolher a versão correta clique em "Export JASON".
 
!!Importante!! para que o **NewMan** consiga executar a Collection precisara formatar o nome dela pois vem no "formato" errado, então siga os passos abaixos
1. Após baixar verifique o nome do arquivo ele ira vir nesse formato `Exemplodenome.retireessaparte.json`;
2. Renomeando devera ficar assim `Exemplodenome.json` foi feito a retirada do `.retireessaparte`;
3. Todo arquivo que foi usar no **NewMan** deverá ficar nesse formato `nome.json`.
---

## Verificando se possui todos os programas necessários
### Após exportar a Collection vamos verificar quais programas você tem para automatizar com o **NewMan** e instalar os que você não tiver
#### Valide se possui o **NODE.JS instalado

1. Para validar Abra o CMD de comando do Windos e digite o seguinte comando;
    ```
    node --version
    ```
2. Se não aparecer a versão do **NODE.JS** significa que você não tem ele instalado. Caso não tenha o **NODE.JS** instalado instale ele atrvés desse link - https://nodejs.org/en/download;
3. Após isso repita o comando "node --version" e veja se aparece a versão.


#### Valide se você possui o **NPM** instalado

1. Para validar Abra o CMD de comando do Windos e digite o seguinte comando;

    ```
    npm --version
    ```

2. Se não aparecer a versão do **NPM** significa que você não tem ele instalado, para fazer a instalação é pelo CMD, basta digitar o seguinte comando;

    ```
    $ npm install download
    ```
3. Após isso repita o comando "npm --version" e veja se aparece a versão.

#### Agora podemos instalar o **NEWMAN** (link com o documento original no final)

1. Para instalar o **NEWMAN** você vai precisar abrir o CMD e inserir o seguinte comando;
```
npm install -g newman
```
2. Após isso insira o comando "newman -version" e veja se aparece a versão.
---

## Com o **NewMan** instalado vamos testar a Collection
### Para Rodar todas as resquest da collection de forma autamatiza siga os passos

0. Verifique se todos os programas necessários estão instalaos e não esqueça de verificar o nome da collection precisar estar no formato exato;
1. Abra o CMD;
2. Acesse o local onde a collection se encontra(no exemplo ela está en downloads);
    - insira o comando abaixo no CMD
    ```
    cd downloads
    ```
    - como resultado o seu endereço no CMD deverá aparecer assim`
    ```
    c:\Users\seuusuário\downloadas>
    ```
3. Digite o seguinte comando `newman run mnomedasuacollection.json` e mande executar.
    - ficara assim no CMD
    ```
    c:\Users\seuusuário\downloadas>newman run mnomedasuacollection.json
    ```
### Interpretando o relátorio do **NewMan**
#### Abaixo estara um relatório gerado em um teste real, após o relatorio estara a explicação

```
├── Consultando usuário sem filtro  
│   GET https://serverest.dev/usuarios [200 OK, 914B, 686ms]

├── Cadastro de usuário  
│   POST https://serverest.dev/usuarios [201 Created, 540B, 177ms]

├── Fazendo login  
│   POST https://serverest.dev/Login [200 OK, 731B, 160ms]

├── Consultando usuário com filtro  
│   GET https://serverest.dev/usuarios?email=testeteste%40hahaha.com [200 OK, 496B, 179ms]

├── Consultando pelo ID  
│   GET https://serverest.dev/usuarios/uGwu2fsuD7fklClh [400 Bad Request, 507B, 167ms]

├── Editando usuário  
│   PUT https://serverest.dev/usuarios/iEjB2ieCZ5E3t0mo [201 Created, 540B, 174ms]

├── Apagando usuário  
│   DELETE https://serverest.dev/usuarios/uGwu2fsuD7fklClh [200 OK, 499B, 172ms]

├── Consultando produtos  
│   GET https://serverest.dev/Produtos [200 OK, 1.69kB, 176ms]

├── Cadastro de novo produto  
│   POST https://serverest.dev/Produtos [401 Unauthorized, 567B, 182ms]

├── Consultando produto por ID  
│   GET https://serverest.dev/Produtos/RgmEyAuCgiTzNrT4 [400 Bad Request, 506B, 197ms]

├── Editando produto  
│   PUT https://serverest.dev/Produtos/RgmEyAuCgiTzNrT4 [401 Unauthorized, 567B, 169ms]

├── Excluindo produto  
│   DELETE https://serverest.dev/Produtos/Tq6cdZj4pDUYkfVn [401 Unauthorized, 567B, 166ms]

├── Consultando carrinhos  
│   GET https://serverest.dev/Carrinhos [200 OK, 1.05kB, 172ms]

├── Cadastrando carrinho  
│   POST https://serverest.dev/Carrinhos [401 Unauthorized, 567B, 169ms]

├── Consultando carrinho por ID  
│   GET https://serverest.dev/Carrinhos/eiYlZ2Pg1p3x7MXH [400 Bad Request, 507B, 160ms]

├── Finalizando compra  
│   DELETE https://serverest.dev/Carrinhos/concluir-compra [401 Unauthorized, 567B, 165ms]

└── Cancelando compra  
    DELETE https://serverest.dev/Carrinhos/cancelar-compra [401 Unauthorized, 567B, 178ms]

| Métrica                  | Executado | Falhou |
| -----------------------  | --------- | ------ |
| Interações               | 1         | 0      |
| Requisições              | 17        | 0      |
| Scripts de teste         | 0         | 0      |
| Scripts pré-requisição   | 0         | 0      |
| Validações (assertions)  | 0         | 0      |

- Estasticas Gerais

Duração total da execução: 4.8s

Total de dados recebidos: 3.57kB (aproximadamente)

Tempo médio de resposta: 202ms

Mínimo: 160ms

Máximo: 686ms

Desvio padrão: 121ms
```

1. Iterações: Número de vezes que a collection foi executada (geralmente 1);
2. Requisições: Quantidade total de endpoints executados durante a rodada;
3. Scripts de Teste (test-scripts)(Não foi utilizado): Scripts escritos em JavaScript que rodam após cada requisição, usados para validar o comportamento esperado da resposta;
4. Scripts pré-requisição (prerequest-scripts)(Não foi utilizado): Scripts que rodam antes de cada requisição, úteis para configurar variáveis ou tokens dinamicamente;
5. Validações (assertions)(Não foi utilizado): São as checagens automáticas feitas nos scripts de teste, que avaliam se uma resposta contém determinado status, campo ou valor esperado.

#### Observações importantes
1. Mesmo com todas as requisições executadas com sucesso (sem falhas), nenhuma validação de teste foi feita porque nenhum script ou assertion foi implementado. Para testar de verdade, é importante adicionar validações no Postman antes de exportar a collection;
2. A maior parte dos erros (400 e 401) aconteceram porque a collection foi executada de forma isolada, sem scripts que armazenem variáveis como ID, token ou dados criados em etapas anteriores. Isso quebra o fluxo de teste automatizado, abaixo segue detalhado cada erro e o porque.

    1. Consultando usuários sem filtro;
    - **Método:** `GET`
    - **Status:** `200 OK`
    - **Motivo:** É uma rota pública, que lista todos os usuários. Não exige autenticação nem parâmetros.

    2. Cadastro de usuário;
    - **Método:** `POST`
    - **Status:** `201 Created`
    - **Motivo:** Usuário criado com sucesso. A resposta traz o `id`, mas ele não foi salvo automaticamente por ausência de script.

    3. Fazendo login;
    - **Método:** `POST`
    - **Status:** `200 OK`
    - **Motivo:** Login efetuado com sucesso. O token de autenticação foi retornado, mas não armazenado em variáveis para uso posterior.

    4. Consultando usuário com filtro (por e-mail);
    - **Método:** `GET`
    - **Status:** `200 OK`
    - **Motivo:** E-mail foi passado corretamente via query param. A requisição não exige autenticação.

    5. Consultando usuário por ID;
    - **Método:** `GET`
    - **Status:** `400 Bad Request`
    - **Motivo:** O `id` informado é inválido ou inexistente. Como o ID do cadastro anterior não foi armazenado, o valor usado foi incorreto.

    6. Editando usuário;
    - **Método:** `PUT`
    - **Status:** `201 Created`
    - **Motivo:** A edição foi feita com um ID válido, mas fixo. Funciona por coincidência, mas não é confiável sem atualização dinâmica.

    7. Apagando usuário;
    - **Método:** `DELETE`
    - **Status:** `200 OK`
    - **Motivo:** O ID ainda existia e pôde ser apagado corretamente. O sucesso pode não se repetir sem controle de variáveis.

    8. Consultando produtos;
    - **Método:** `GET`
    - **Status:** `200 OK`
    - **Motivo:** Rota pública. Lista todos os produtos sem exigir token ou parâmetros.

    9. Cadastro de produto;
    - **Método:** `POST`
    - **Status:** `401 Unauthorized`
    - **Motivo:** Falta de autenticação. O token de admin não foi incluído no header, então o cadastro foi recusado.

    10. Consultando produto por ID;
        - **Método:** `GET`
        - **Status:** `400 Bad Request`
        - **Motivo:** O produto não foi cadastrado (passo 9 falhou), então o ID informado não existe.

    11. Editando produto;
        - **Método:** `PUT`
        - **Status:** `401 Unauthorized`
        - **Motivo:** Também requer autenticação de admin. Sem token, a requisição é negada.

    12. Excluindo produto;
        - **Método:** `DELETE`
        - **Status:** `401 Unauthorized`
        - **Motivo:** Mesmo motivo do anterior. A falta do token de admin impede a operação.

    13. Consultando carrinhos;
        - **Método:** `GET`
        - **Status:** `200 OK`
        - **Motivo:** A listagem de carrinhos é pública. Não exige autenticação.

    14. Cadastro de carrinho;
        - **Método:** `POST`
        - **Status:** `401 Unauthorized`
        - **Motivo:** Exige login. Como o token da etapa de login não foi salvo, a requisição falhou.

    15. Consultando carrinho por ID;
        - **Método:** `GET`
        - **Status:** `400 Bad Request`
        - **Motivo:** O ID de carrinho usado não existe, pois o carrinho não foi criado com sucesso na etapa anterior.

    16. Finalizando compra;
        - **Método:** `DELETE`
        - **Status:** `401 Unauthorized`
        - **Motivo:** Exige autenticação e carrinho válido. Como nenhum foi criado, e não há token, a ação falha.

    17. Cancelando compra.
        - **Método:** `DELETE`
        - **Status:** `401 Unauthorized`
        - **Motivo:** Mesma situação do item anterior. Sem login e sem carrinho, a requisição é negada.

3. A maior parte dos erros (`400 Bad Request` e `401 Unauthorized`) ocorreram por falta de **encadeamento lógico entre as requisições**, especialmente na ausência de scripts para salvar e reutilizar `id` e `token`. As requisições foram executadas de forma isolada, sem reaproveitamento dinâmico de dados entre as etapas.
4. Possiveis soluções a serem estudadas e aplicadas
    - Usar **scripts de teste no Postman** para capturar variáveis (`token`, `id`, etc.).
    - Armazenar e reutilizar variáveis com `pm.environment.set()` e `{{variavel}}`.
    - Adicionar **validações (assertions)** para checar se os retornos estão corretos antes de seguir para o próximo passo.

**Fim do documento obrigado pela leitura**

Links dos documentos originais consultados
https://www.npmjs.com/package/download
https://learning.postman.com/docs/collections/using-newman-cli/installing-running-newman/

Link Serverest completo com a API completa:
https://serverest.dev/#/

Para deixar seus projetos mais interessantes, utilize o formato markdown. Segue alguns sites utilizando essa formatação:
- [dillinger.io](https://dillinger.io/)
- [Markdownlivepreview](https://markdownlivepreview.com/)
- [stackedit.io](https://stackedit.io/app#) ✨