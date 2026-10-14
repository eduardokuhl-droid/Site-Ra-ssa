# Site da Raissa Andrade: fisioterapia pélvica

Site de [raissaandradefisio.com](https://www.raissaandradefisio.com), aprovado pela Raissa em outubro de 2026.

É um site **estático**: HTML e imagens, sem build, sem framework e sem dependências. O que está neste repositório é exatamente o que vai para o ar.

```
index.html                    ← página principal
politica-de-privacidade.html  ← link do rodapé
favicon.svg                   ← ícone da aba
robots.txt e sitemap.xml      ← para o Google
img/                          ← fotos, imagem de compartilhamento (og-image.jpg) e ícone do celular
```

## Como colocar no ar (João)

O jeito mais fácil é ligar este repositório a uma hospedagem que publica sozinha a cada alteração.

### Opção A: Vercel ou Netlify (recomendado)

1. Faça um **backup** do site atual (o projeto Vite que está no ar hoje).
2. Na Vercel: **Add New → Project → Import** este repositório. Na Netlify: **Add new site → Import an existing project**.
3. Configuração:
   - **Framework:** Other (Vercel) ou nenhum (Netlify)
   - **Build command:** deixe vazio
   - **Output / publish directory:** `.` (a raiz)
4. Em **Domains**, aponte `raissaandradefisio.com` e `www.raissaandradefisio.com` para o projeto novo e tire o domínio do projeto antigo.
5. Pronto. A partir de agora, **cada commit na branch `main` atualiza o site sozinho**.

### Opção B: hospedagem tradicional (Hostinger, Locaweb etc.)

Baixe o repositório (**Code → Download ZIP**), faça backup de `public_html` e envie estes arquivos para lá, com `index.html` na raiz.

## Depois de publicar, teste

- [ ] Abrir no celular e no computador
- [ ] Clicar em todos os botões de WhatsApp: devem abrir uma conversa com o (11) 99460-3791 e a mensagem pronta
- [ ] Mandar o link no WhatsApp para alguém e ver se aparece a prévia com a foto (pode levar alguns minutos)
- [ ] Abrir a política de privacidade pelo rodapé
- [ ] Conferir o HTTPS e se o endereço com e sem `www` abre o mesmo site

## Google (15 minutos)

1. **Google Search Console:** envie `https://www.raissaandradefisio.com/sitemap.xml` em "Sitemaps".
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

## Para editar no futuro

Está tudo no `index.html`, em português e em ordem: topo, "Como eu ajudo", "Como funciona", "Por que comigo", "Quem sou", "No dia a dia", depoimentos, regiões, dúvidas e rodapé. As cores ficam no começo do arquivo, em `:root`. Dá para editar direto pelo GitHub (ícone de lápis), e o site atualiza sozinho.

**Fotos de pacientes** (`img/atendimento-gestante.jpg` e `img/kinesio-gestante.jpg`, na seção "No dia a dia"): só ficam no ar com autorização por escrito das pacientes. Para tirar uma delas, apague o bloco `<figure>` correspondente no `index.html`.

Dúvidas: fala com o Eduardo.
