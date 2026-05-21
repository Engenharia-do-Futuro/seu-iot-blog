# seu-iot-blog

Repositório público que serve como CMS estático para o blog da plataforma [Seu IoT](https://seuiot.com.br).

O conteúdo é consumido diretamente pelo web-client via GitHub Raw Content API — sem back-end, sem build, sem custo.

## Como funciona

O web-client faz até quatro requisições por visita:

1. `GET {base}/index.json` — lista todos os posts
2. `GET {base}/{post.content[lang]}` — carrega o markdown do post aberto
3. `GET {base}/{post.author.bio[lang]}` — carrega a bio do autor (opcional)
4. `GET {base}/{post.author.avatar}` — foto do autor (opcional)

O markdown é renderizado pelo parser já existente no projeto.

**URL base:**
```
https://raw.githubusercontent.com/Eng-Do-Futuro/seu-iot-blog/main/
```

## Estrutura

```
seu-iot-blog/
  index.json              # índice de todos os posts (mais recente primeiro)
  posts/
    release/               # posts de release notes / novidades da plataforma
      {version}-{slug}/
        pt-br.md
        en-us.md
        images/            # imagens usadas no post (opcional)
  authors/
    {Author_Name}/
      {Author_Name}.png   # foto do autor
      pt-br.md            # mini bio em português
      en-us.md            # mini bio em inglês
  images/
    seuiot_common/        # imagens compartilhadas entre posts
```

## Adicionando um post

1. Crie a pasta seguindo o padrão da categoria (veja abaixo)
2. Adicione `pt-br.md` e `en-us.md` com o conteúdo em markdown
3. Adicione as imagens do post em `images/` dentro da pasta do post
4. Insira a entrada no topo do `index.json`, incluindo o campo `author`

## Adicionando um autor

1. Crie a pasta `authors/{Author_Name}/`
2. Adicione a foto `{Author_Name}.png`
3. Adicione `pt-br.md` e `en-us.md` com a mini bio

### Categorias e padrão de pasta

| Categoria | Pasta | Exemplo |
|-----------|-------|---------|
| `release`  | `posts/release/{version}-{slug}/` | `posts/release/0.16.2-ble-personnas-provisionamento/` |

## Schema do `index.json`

```json
{
  "slug": "identificador-unico-usado-na-url",
  "date": "YYYY-MM-DD",
  "category": "release",
  "tags": ["array", "de", "strings"],
  "title": { "pt": "Título", "en": "Title" },
  "subtitle": { "pt": "Resumo curto.", "en": "Short summary." },
  "content": {
    "pt": "posts/release/{version}-{slug}/pt-br.md",
    "en": "posts/release/{version}-{slug}/en-us.md"
  },
  "author": {
    "name": "Nome do Autor",
    "avatar": "authors/{Author_Name}/{Author_Name}.png",
    "bio": {
      "pt": "authors/{Author_Name}/pt-br.md",
      "en": "authors/{Author_Name}/en-us.md"
    }
  }
}
```

---

Acesse a plataforma em [seuiot.com.br](https://seuiot.com.br).
