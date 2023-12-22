# API da Gigahertz

A [Gigahertz](https://gigahertz.fm) disponibiliza uma API que da acesso ao conteúdo da rede, incluindo listas de podcasts, detalhes de cada podcast, listas de episódios, detalhes de cada episódio, entre outras informações.

**Importante: A API ainda não é considerada estável, portanto o formato das respostas e disponibilidade de endpoints pode variar ao longo do tempo. Tentaremos manter este repositório atualizado sempre que houver alterações.**

## Endpoints

Todos os endpoints utilizam a URL base `https://gigahertz.fm/api/`, as respostas são sempre em formato JSON. As requisições devem ser sempre `https`.

### `https://gigahertz.fm/api/podcasts.json`

Este endpoint recupera informações básicas sobre os podcasts publicados pela Gigahertz.

### podcasts

Um array de objetos de podcast, cada um contendo:

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
