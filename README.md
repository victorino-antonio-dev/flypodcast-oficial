# Fly Podcast – Website

Site estático (HTML, CSS e JavaScript em ficheiros simples, sem build) com o Mural da semana, a Ficha do Convidado e a secção sobre o Fly Skuad.

## Estrutura

```
index.html     página única (CSS e JS incluídos)
assets/        logótipo, favicon e fotografias
_headers       cabeçalhos de segurança e cache (Cloudflare)
```

## Publicar no GitHub

```bash
git init
git add .
git commit -m "Website Fly Podcast"
git branch -M main
git remote add origin https://github.com/SEU_UTILIZADOR/flypodcast-site.git
git push -u origin main
```

(Crie antes o repositório vazio em github.com/new, sem README.)

## Publicar no Cloudflare Pages

1. Cloudflare Dashboard → **Workers & Pages** → **Create** → **Pages** → **Connect to Git**.
2. Escolha o repositório `flypodcast-site`.
3. Configuração: **Framework preset:** None · **Build command:** (vazio) · **Build output directory:** `/`
4. **Save and Deploy**. O site fica em `https://NOME.pages.dev` e cada `git push` publica de novo.
5. Domínio próprio: projeto → **Custom domains** → **Set up a domain**.

## Como atualizar os convidados

No fim de `index.html`, o array `G` tem um objeto por convidado (dia, data com fuso `+01:00` de Luanda, estado, perfil, linha do tempo, temas, recomendações). A contagem decrescente usa o primeiro convidado da lista.

Estados disponíveis: `HOJE EM DIRETO` (`cls:"live"`), `CONFIRMADO` (`ok`), `AGENDADO` (`sch`), `JÁ DISPONÍVEL` (`done`).

## A fazer antes de ir para produção

- Substituir os convidados de exemplo por dados validados (o Dr. Laurindo Ngola é fictício).
- A caixa de perguntas só mostra o texto no ecrã. Para guardar as perguntas, ligar a um serviço (Cloudflare Pages Functions + D1, Formspree, etc.).
- Trocar `og:image` por um URL absoluto (`https://SEU_DOMINIO/assets/cartaz-hero.jpg`) para as pré-visualizações em redes sociais.
