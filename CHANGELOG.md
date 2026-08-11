# Changelog

Formato baseado em [Keep a Changelog](https://keepachangelog.com/pt-BR/1.0.0/).
Versionamento: [Semantic Versioning](https://semver.org/lang/pt-BR/) (`MAJOR.MINOR.PATCH`).

## [3.9.3]
### Fixed
- Exportação "só códigos" (.txt) do lote não repetia códigos duplicados. Causa: a exportação usava a lista já agrupada por código único, ignorando o campo de contagem (`count`). Cada código passa a ser repetido conforme o número real de vezes escaneado.

## [3.9.2]
### Changed
- Removidas todas as referências ao nome de empresa anteriormente hardcoded no código (título, cabeçalho, exportações `.txt`).
- Adicionados hyperlinks na seção "Sobre": autor → GitHub, licença → mit-license.org.

## [3.9.1]
### Changed
- Texto da seção "Sobre" atualizado (autoria, uso interno, nota de desenvolvimento assistido por IA).

## [3.9.0]
### Added
- Menu hambúrguer no cabeçalho com dropdown.
- Seção "Inventário" (placeholder, funcionalidade futura).
- Seção "Sobre" (créditos, versão, licença).

## [3.8.1]
### Fixed
- Login não avançava para o app na build que roda em `window.storage` (artefato Claude). Causa: uso de `sessionStorage`, API não suportada nesse ambiente. Sessão agora mantida em variável de memória nessa build; a build offline mantém `sessionStorage`.

## [3.8.0]
### Added
- Tela de autenticação (usuário/senha) antes do acesso ao app, com logout.
- Autenticação implementada como stub local (aceita qualquer credencial não vazia); ponto de integração para backend real documentado no código-fonte.

### Changed
- Nomes de arquivo exportados passam a incluir o número de versão.

## [3.7.3]
### Fixed
- Overflow horizontal na listagem de produtos (grid de 2 colunas, desktop). Causa: item de CSS Grid sem `min-width:0`, impedindo encolhimento abaixo da largura do conteúdo.

## [3.7.2]
### Fixed
- Lag ao expandir a seção "Base de produtos" no desktop. Causa: `column-count` (CSS multi-coluna) força recálculo de balanceamento de colunas ao sair de `display:none`. Substituído por CSS Grid.

## [3.7.1]
### Changed
- Feedback de progresso da importação de CSV: texto discreto substituído por barra de progresso com maior contraste visual.

## [3.7.0]
### Added
- Feedback de progresso em tempo real durante importação de CSV (processamento em blocos, sem travar a UI).
- Estados vazios com call-to-action: lista de produtos vazia e resultado "não cadastrado" (quando a base está vazia) agora oferecem atalho direto para importação.

## [3.6.1]
### Fixed
- Alinhamento vertical do texto na seção de importação (margem superior de parágrafo não zerada).

## [3.6.0]
### Fixed
- Normalização de zeros à esquerda na comparação de códigos de barras (`12345` == `012345`), cobrindo divergências entre simbologias UPC-A/EAN-13.

## [3.5.1]
### Fixed
- Alinhamento entre colunas no layout desktop (verificação individual vs. lote).

## [3.5.0]
### Added
- Layout responsivo de duas colunas para desktop (≥900px): verificação individual e em lote lado a lado; lista de produtos em grid de 2 colunas.

## [3.4.0]
### Added
- Build offline (`localStorage` no lugar de `window.storage`), para execução fora do ambiente Claude.

## [3.3.0]
### Changed
- Seção "Verificação em lote" sempre visível (removido toggle de expandir/recolher).

## [3.2.0]
### Added
- Segunda opção de exportação `.txt` no lote: códigos sem formatação/cabeçalho, além da exportação já existente com status e metadados.

## [3.1.0]
### Changed
- Seção de importação de CSV reposicionada para antes do campo de busca.

## [3.0.0]
### Removed
- Formulário de cadastro manual (adicionar/editar produto individualmente). Base de dados passa a ser alimentada exclusivamente via importação de CSV.

## [2.6.0]
### Added
- Campo "Referência" em toda a aplicação (formulário, importação, verificação individual/lote, exportações).

## [2.5.0]
### Changed
- Verificação em lote agrupa códigos duplicados, exibindo contagem (`× N`) em vez de linhas repetidas.

## [2.4.0]
### Added
- Opção de minimizar a lista de produtos cadastrados.
### Changed
- Paleta de cores migrada para escala de cinza (preto/branco/cinza).

## [2.3.0]
### Changed
- Unificação do campo de busca e área de resultado em um único componente visual.

## [2.2.0]
### Added
- Reexibição de detalhes do produto (descrição, categoria, tamanho, cor) no resultado da verificação.

## [2.1.0]
### Added
- Importação de CSV com suporte a múltiplos códigos de barras por produto (delimitador `|`).

## [2.0.0]
### Changed
- Conceito da aplicação alterado de busca de produto (exibição de descrição completa) para verificação binária de existência do código na base.

## [1.1.0]
### Added
- Verificação em lote (múltiplos códigos via textarea) e exportação de resultados em `.txt`.

## [1.0.0]
### Added
- Lançamento inicial: busca de produto por código de barras, CRUD manual, armazenamento persistente.

