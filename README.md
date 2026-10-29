# Ponto de Ruptura

Site estático: sem build, sem dependências, sem servidor.

```
index.html              o jogo inteiro
assets/img/*.webp       29 imagens
assets/video/*.mp4      loops de fundo (5 horizontais prontos)
assets/audio/*.mp3      ambiente por ato (opcional)
```

## Publicar

**GitHub Pages:** envie na raiz do repositório → Settings → Pages → branch `main`, pasta `/ (root)`.

**Cloudflare Pages:** Workers & Pages → Create → Pages → conectar o repositório.
Build command **vazio**, output directory **`/`**.

## Importante: não abra direto no navegador por duplo clique

Abrir `index.html` como arquivo local (`file://`) faz alguns navegadores bloquearem
o carregamento de `assets/video/*.mp4` por política de segurança, mesmo com os
arquivos na pasta certa. Para testar localmente, sirva por HTTP:

```bash
cd ponto-de-ruptura
python3 -m http.server 8000
```

E abra `http://localhost:8000`. No GitHub Pages ou Cloudflare isso não é um
problema, porque o site já é servido por HTTP normalmente.

## Vídeos

Já incluídos: `ato1-h.mp4` até `ato5-h.mp4`, em 1376×768, sem áudio, cerca de 700 kB cada.

**A proporção é obrigatória: 1376 × 768.** Os cliques nas pastas são polígonos medidos
sobre a imagem; se o vídeo tiver outra proporção, o enquadramento muda e os contornos
saem do lugar.

**Como toca:** uma vez do começo ao fim, depois segura o último quadro por 30 segundos,
depois recomeça. Como o primeiro quadro é igual ao último e igual à foto estática,
não há salto em nenhuma das transições.

**Verticais:** ainda não existem. No celular o jogo usa a foto estática.
Quando os `ato1-v.mp4` até `ato5-v.mp4` existirem, acrescente as chaves `"1v"` a `"5v"`
no objeto `VIDEOS` e remova a checagem `!vertical()` de `movimentoOk()`.

## Som ambiente

`assets/audio/amb-ato1.mp3` até `amb-ato5.mp3`. De 60 a 90 s, mono, 96 kbps,
em loop, sem música e sem voz. O que faltar simplesmente não toca.

## Compatibilidade

Chrome, Edge, Firefox e Safari, desktop e celular. A narração usa a síntese de voz
do navegador e não funciona no Firefox.
