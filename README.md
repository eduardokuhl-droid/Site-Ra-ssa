# Site novo da Raissa: como colocar no ar

Oi, João! Este pacote tem o site novo completo, já aprovado pela Raissa. É um site **estático**: HTML e imagens, sem build, sem framework e sem dependências. É só publicar os arquivos.

## O que tem no pacote

```
index.html                    ← página principal
politica-de-privacidade.html  ← link do rodapé
favicon.svg                   ← ícone da aba
robots.txt e sitemap.xml      ← para o Google
img/                          ← fotos, imagem de compartilhamento (og-image.jpg) e ícone do celular
```

## Passo a passo

1. **Faça um backup do site atual** (o projeto Vite que está no ar hoje), para poder voltar se precisar.
2. **Troque o conteúdo publicado** no domínio `raissaandradefisio.com` pelos arquivos deste pacote, com `index.html` na raiz.
   - **Vercel ou Netlify:** crie um deploy novo com esta pasta (não precisa de comando de build; a pasta de saída é a própria raiz) e aponte o domínio para ele. Outra opção é substituir o conteúdo de `dist/` do projeto atual.
   - **Hospedagem tradicional (Hostinger, Locaweb etc.):** apague os arquivos antigos de `public_html` (depois do backup) e envie estes.
3. **Confira o HTTPS** e se `www.raissaandradefisio.com` e `raissaandradefisio.com` abrem o mesmo site.

## Depois de publicar, teste

- [ ] Abrir no celular e no computador
- [ ] Clicar em todos os botões de WhatsApp: devem abrir uma conversa com o (11) 99460-3791 e a mensagem pronta
- [ ] Mandar o link no WhatsApp para alguém e ver se aparece a prévia com a foto (pode levar alguns minutos)
- [ ] Abrir a política de privacidade pelo rodapé
- [ ] Ver o ícone "R" na aba do navegador

## Google (15 minutos)

1. **Google Search Console:** adicione o domínio (se ainda não estiver) e envie `https://www.raissaandradefisio.com/sitemap.xml` em "Sitemaps".
2. **Google Analytics (GA4):** crie uma propriedade para a Raissa e cole o código `gtag.js` no `<head>` do `index.html`, no lugar do comentário `<!-- Google Analytics ... -->`. Para medir os cliques no WhatsApp, cole também isto logo antes de `</body>`:

```html
<script>
  document.querySelectorAll('a[href*="wa.me"]').forEach(function (a) {
    a.addEventListener('click', function () {
      if (window.gtag) gtag('event', 'clique_whatsapp');
    });
  });
</script>
```

3. **Perfil da Empresa no Google:** coloque `https://www.raissaandradefisio.com` no campo "Website". Hoje o perfil está sem site.

## Para editar textos no futuro

Está tudo no `index.html`, em português e em ordem: topo, "Como eu ajudo", "Como funciona", "Por que comigo", "Quem sou", "No dia a dia", depoimentos, regiões, dúvidas e rodapé. As cores ficam no começo do arquivo, em `:root`.

**Fotos de pacientes** (`img/atendimento-gestante.jpg` e `img/kinesio-gestante.jpg`, na seção "No dia a dia"): só podem ficar no ar com autorização por escrito das pacientes. Se precisar tirar alguma, apague o bloco `<figure>` correspondente no `index.html`.

Qualquer dúvida, fala com o Eduardo.
