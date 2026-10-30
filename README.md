# Ponto de Ruptura

Site estático: sem build, sem dependências, sem servidor.

```
index.html              o jogo inteiro
assets/img/*.webp       salas, arquivos, insígnias e (quando houver) fundos dos finais
assets/video/*.mp4      loops de fundo das salas
assets/audio/*.mp3      trilha, músicas dos finais e ambientes
```

## Publicar

**GitHub Pages:** envie na raiz → Settings → Pages → branch `main`, pasta `/ (root)`.
**Cloudflare Pages:** conectar o repositório, build command **vazio**, output **`/`**.

Para testar no computador, não abra o `index.html` com duplo clique: rode
`python3 -m http.server 8000` dentro da pasta e acesse `http://localhost:8000`.

## Arquivos que ainda podem entrar

| Arquivo | Onde | O que é |
| --- | --- | --- |
| `trilha.mp3` | `assets/audio/` | Música contínua do jogo todo, em loop |
| `final-a.mp3` … `final-d.mp3` | `assets/audio/` | Uma peça por final, sem loop |
| `amb-ato1.mp3` … `amb-ato5.mp3` | `assets/audio/` | Ambiente de cada sala, em loop |
| `final-a-h.webp` … `final-d-v.webp` | `assets/img/` | Fundo de cada final, desktop e celular |
| `ato1-v.mp4` … `ato5-v.mp4` | `assets/video/` | Loops verticais (ainda não ligados) |

**Tudo é opcional:** o que faltar cai no provisório sem erro.

**Volumes já calibrados no código:** trilha 35%, ambiente 34%, música do final 55%.
A trilha some em 1,8 s quando o final começa, e a música do final entra junto com o título.

## Vídeos das salas

1376 × 768 obrigatório — os cliques nas pastas são medidos sobre a imagem.
Tocam uma vez, seguram o último quadro por 30 s e recomeçam.
