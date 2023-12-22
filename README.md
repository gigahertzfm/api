# API da Gigahertz

A [Gigahertz](https://gigahertz.fm) disponibiliza uma API que da acesso ao conteúdo da rede, incluindo listas de podcasts, detalhes de cada podcast, listas de episódios, detalhes de cada episódio, entre outras informações.

## Status da API

**A API ainda não é considerada estável**. O formato das respostas e disponibilidade de endpoints pode variar ao longo do tempo. Tentaremos manter este repositório atualizado sempre que houver alterações.

Podem existir informações adicionais nas respostas da API que não estão documentadas neste reposiório. Evite usar essas informações não-documentadas, pois a chance de mudarem ou deixarem de existir é grande.

## Endpoints

Todos os endpoints utilizam a URL base `https://gigahertz.fm/api/`, as respostas são sempre em formato JSON. As requisições devem ser sempre `https`.

## Lista de podcasts: `podcasts.json`

Este endpoint recupera informações básicas sobre os podcasts publicados pela Gigahertz.

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

Este endpoint fornece informações detalhadas sobre o podcast um podcast específico. O parâmetro `slug` corresponde ao `slug` retornado na API `podcasts`.

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
