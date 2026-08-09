# Verificador de Código de Barras

Ferramenta web para conferência rápida de códigos de barras contra uma base de produtos importada via CSV. Pensada para uso em varejo — recebimento de mercadoria, conferência de estoque e consulta de produtos — mas sem dependências específicas de negócio.

Aplicação single-file (HTML + CSS + JS, sem build, sem dependências externas além de fontes web), disponível em duas builds:

| Build | Arquivo | Armazenamento | Onde roda |
|---|---|---|---|
| Claude | `verificador-codigo-barras-vX.Y.Z.html` | `window.storage` (API de artefatos do Claude) | Dentro do claude.ai, como artefato |
| Offline | `verificador-codigo-barras-offline-vX.Y.Z.html` | `localStorage` do navegador | Qualquer navegador — duplo clique no arquivo, Live Server, servidor local, etc. |

As duas builds têm as mesmas funcionalidades; a única diferença é a camada de armazenamento dos dados.

## Funcionalidades

- **Verificação individual** — digite ou escaneie um código de barras e veja na hora se está cadastrado, com descrição, referência, categoria, tamanho e cor.
- **Verificação em lote** — cole ou escaneie vários códigos (um por linha); a lista agrupa repetidos e mostra quantos foram encontrados/não encontrados.
- **Importação via CSV** — suporta múltiplos códigos de barras por produto (delimitador `|`), com barra de progresso durante a importação.
- **Exportação em `.txt`** — resultado completo (com status/quantidade/referência) ou lista crua de códigos, tanto na verificação individual quanto em lote.
- **Normalização de código** — zeros à esquerda são ignorados na comparação (`12345` == `012345`), cobrindo divergências entre simbologias UPC-A/EAN-13.
- **Layout responsivo** — coluna única no mobile; duas colunas (verificação individual + lote lado a lado) a partir de 900px.
- **Autenticação** — tela de login antes do acesso ao app (ver [Autenticação](#autenticação) abaixo).

## Como usar

### Build Claude
Suba o arquivo `.html` como artefato numa conversa do Claude, ou peça pro Claude recriar/editar a partir dele.

### Build offline
Baixe o arquivo `-offline-` e abra direto no navegador (duplo clique), ou sirva localmente com qualquer servidor estático (ex: extensão Live Server do VS Code). Não precisa de Node, build step ou instalação — é HTML puro.

## Formato do CSV esperado

O importador reconhece as seguintes colunas por nome (não precisam estar em ordem específica):

| Coluna | Obrigatória | Observações |
|---|---|---|
| `Códigos de Barras` | Sim | Múltiplos códigos do mesmo produto separados por `\|` |
| `Descrição` | Sim | |
| `Linha` | Não | Usada como categoria |
| `Tamanho` | Não | |
| `Cor` | Não | |
| `Referência` | Não | |

Linhas sem `Descrição` ou `Códigos de Barras` são ignoradas na importação.

## Autenticação

A tela de login está pronta na interface, mas hoje usa um **stub local** (aceita qualquer usuário/senha não vazios) — ainda não há backend de autenticação real. O ponto de integração está isolado na função `authenticateUser()` do código-fonte, com instruções em comentário sobre como substituir por uma chamada de API real quando o backend estiver disponível.

## Versionamento

Segue [Semantic Versioning](https://semver.org/lang/pt-BR/). Histórico completo em [`CHANGELOG.md`](./CHANGELOG.md).

## Créditos

Desenvolvido por [Guilherme Alcântara](https://github.com/tr-cross), com apoio de IA (Claude, Anthropic) no processo de desenvolvimento.

## Licença

Distribuído sob a licença MIT. Veja [`LICENSE`](./LICENSE) para o texto completo.
