# API da Gigahertz

A [Gigahertz](https://gigahertz.fm) disponibiliza uma API que da acesso ao conteúdo da rede, incluindo listas de podcasts, detalhes de cada podcast, listas de episódios, detalhes de cada episódio, entre outras informações.

## Termos de Uso

Disponibilizamos a API como forma de facilitar o desenvolvimento de ferramentas que dão acesso ao conteúdo da Gigahertz. Não há nenhuma garantia sobre seu funcionamento ou continuidade da sua existência.

A API não pode ser utilizada para fins comerciais e a utilização da mesma não permite o uso da marca Gigahertz, logotipos, capas e trilhas sonoras dos podcasts, que são protegidos por copyright.

Caso tenha dúvidas sobre sua ideia de uso da API, [poste na área de perguntas e respostas](https://github.com/gigahertzfm/api/discussions/new?category=ideias).

## Status da API

**A API ainda não é considerada estável**. O formato das respostas e disponibilidade de endpoints pode variar ao longo do tempo. Tentaremos manter este repositório atualizado sempre que houver alterações.

Podem existir informações adicionais nas respostas da API que não estão documentadas neste reposiório. Evite usar essas informações não-documentadas, pois a chance de mudarem ou deixarem de existir é grande.

## Endpoints

Todos os endpoints, exceto o de transcrição, utilizam a URL base `https://gigahertz.fm/api/`, as respostas são sempre em formato JSON. As requisições devem ser sempre `https`.

## Lista de podcasts: `podcasts.json`

Este endpoint recupera informações básicas sobre os podcasts publicados pela Gigahertz.

Exemplo: https://gigahertz.fm/api/podcasts.json

### Resposta

- **podcasts**: Um array de objetos de podcast, cada um contendo:
    - **artworkVariants**: Diferentes imagens de arte do podcast, categorizadas por tipo (`fullBleed`, `square`, `wallpaperHero`) e tamanho (`high` ou `medium`, com variantes 1x, 2x, 3x).
    - **body**: Descrição ou texto do corpo do podcast.
    - **category**: A categoria do podcast no Apple Podcasts (por exemplo, "Technology").
    - **subcategory**: A subcategoria do podcast no Apple Podcasts (por exemplo, "Tech News").
    - **colors**: Várias configurações de cor usadas no tema do podcast, como `backdropTintRGBA`, `link`, `navigationBarTint` e `primary`.
    - **date**: A data de lançamento do primeiro episódio do podcast.
    - **episodeCount**: O número total de episódios do podcast.
    - **hosts**: Um array de apresentadores do podcast, cada um incluindo detalhes como `avatarURL`, `firstName`, `fullName`, `id`, `permalink` e `socialProfiles`.
    - **id**: Um identificador único para o podcast.
    - **latestEpisode**: Informações sobre o episódio mais recente, incluindo `date`, `episodeNumber`, `guid`, `id` e `permalink`.
    - **permalink**: Um link permanente para a home do podcast no site da Gigahertz.
    - **schedule**: O dia da semana quando são lançados novos episódios do podcast.
    - **shortTitle**: Um título mais curto/informal do podcast.
    - **slug**: Uma versão amigável do título do podcast para URLs.
    - **socialProfiles**: Links para os perfis de mídia social do podcast.
    - **subscriptionLinks**: Links para várias plataformas onde o podcast pode ser assinado ou ouvido.
    - **synopsis**: Uma breve descrição do podcast.
    - **tagline**: O slogan/subtítulo do podcast.
    - **title**: O título do podcast.
    - **updatedAt**: A última data e hora da atualização das informações do podcast.

## Detalhes do podcast: `podcasts/{slug}/index.json`

Este endpoint fornece informações detalhadas sobre um podcast específico. O parâmetro `slug` corresponde ao `slug` retornado na API `podcasts`.

Exemplo: `https://gigahertz.fm/api/podcasts/adt/index.json`

### Resposta

- **additionalLinks**: Um array de links adicionais relacionados ao podcast, cada um contendo:
  - `title`: O título do link.
  - `url`: O URL do link.
- **artworkVariants**: Variantes de arte do podcast, incluindo `fullBleed`, `square` e `wallpaperHero`, cada um com versões de alta (`high`) e média (`medium`) resolução.
- **colors**: Cores usadas na temática do podcast, incluindo `backdropTintRGBA`, `link`, `navigationBarTint` e `primary`.
- **date**: Data de criação do podcast.
- **episodes**: Um array de episódios do podcast, cada um com detalhes como `date`, `episodeNumber`, `guid`, `id`, `permalink`, `summary`, `title` e `updatedAt`.
- **id**: Identificador único do podcast.
- **shortTitle**: Título curto do podcast.
- **tagline**: Slogan do podcast.
- **title**: Título do podcast.
- **updatedAt**: Data da última atualização das informações do podcast.

## Detalhes do episódio: `podcasts/{slug}/{episodeNumber}.json`

Este endpoint fornece informações detalhadas sobre um episódio específico, onde `slug` é o `slug` do podcast e `episodeNumber` é o número do episódio.

Exemplo: `https://gigahertz.fm/api/podcasts/adt/356.json`

### Resposta

- **audio**: Detalhes do arquivo de áudio do episódio, incluindo:
  - `byteSize`: Tamanho do arquivo em bytes.
  - `duration`: Duração do episódio, com horas, minutos e segundos.
  - `formattedByteSize`: Tamanho do arquivo formatado (exemplo: "96.2 MB").
  - `formattedDuration`: Duração formatada do episódio (exemplo: "01:39:56").
  - `url`: URL do arquivo de áudio do episódio.
- **body**: Notas do episódio em HTML.
- **date**: Data e hora de publicação do episódio.
- **episodeNumber**: Número do episódio.
- **guests**: Lista de convidados do episódio (se houver).
- **guid**: Identificador global único do episódio.
- **hosts**: Lista de apresentadores do episódio, incluindo detalhes como `avatarURL`, `firstName`, `fullName`, `id`, `permalink` e `socialProfiles`; incluí somente os participantes do episódio, não necessariamente todos os hosts do podcast
- **id**: Identificador único do episódio.
- **permalink**: Link permanente para o episódio no site da Gigahertz.
- **sponsors**: Lista de patrocinadores do episódio, com nome e URL.
- **summary**: Descrição curta do episódio.
- **title**: Título do episódio.
- **updatedAt**: Data da última atualização das informações do episódio.

## Transcrição do episódio

Este é o único endpoint que não faz parte da API JSON. Para acessar a transcrição de um episódio, basta acessá-lo no site (ou obter o permalink via API) e adicionar `.txt` no final da URL.

### Exemplo

A URL do episódio 78 do Área de Trabalho é `https://gigahertz.fm/podcasts/adtrabalho/78`.

Acessando `https://gigahertz.fm/podcasts/adtrabalho/78.txt`, o site responde com uma versão em texto puro da transcrição.

> **NOTA:** como as transcrições são automáticas, podem existir erros em diversas palavras e informações adicionais "alucinadas" pelo modelo, especialmente no final da transcrição. Alguns episódios podem conter falhas técnicas na transcrição, incluindo problemas de encoding ou falas repetidas. Se encontrar esses problemas de encoding e/ou falas repetidas, por favor nos avise através do link de feedback no site da Gigahertz.