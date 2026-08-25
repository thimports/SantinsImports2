# Santins Imports — loja virtual

Site estático completo. Não precisa de build, framework ou instalação.

## Estrutura

```
index.html          Home
catalogo.html       Catálogo
nb530.html          New Balance 530 White / Natural Indigo
nb9060.html         New Balance 9060 Triple Black
crocs.html          Crocs Classic Clog x The Cars Lightning McQueen
smartwatch.html     SmartWatch GPS 1.43" AMOLED
sobre.html          Sobre nós
contato.html        Atendimento
faq.html            Dúvidas frequentes
rastreio.html       Rastrear pedido
trocas.html         Trocas e devoluções
entrega.html        Política de entrega
pagamento.html      Formas de pagamento
privacidade.html    Política de privacidade
termos.html         Termos de uso

Header.dc.html      Cabeçalho (componente compartilhado)
Footer.dc.html      Rodapé (componente compartilhado)
support.js          Runtime dos componentes
assets/             Todas as imagens e vídeos otimizados (usados pelo site)
uploads/            Arquivos originais, em alta. Nenhuma página do site usa esta pasta.
*.dc.html           Arquivos de origem do canvas. Não fazem parte do site publicado.
vercel.json         Configuração (URLs sem .html)
```

## Subir no GitHub

```bash
git init
git add .
git commit -m "Santins Imports"
git branch -M main
git remote add origin https://github.com/SEU-USUARIO/santins-imports.git
git push -u origin main
```

## Hospedar na Vercel

1. Acesse vercel.com e clique em **Add New → Project**
2. Importe o repositório
3. Framework Preset: **Other**
4. Build Command: deixe **vazio**
5. Output Directory: deixe **vazio** (raiz)
6. Deploy

Com o `vercel.json` incluído, as URLs ficam limpas: `/nb530`, `/catalogo`, `/faq`.

## Observação importante

As páginas carregam o cabeçalho e o rodapé por requisição HTTP. Abrir os arquivos
com duplo clique (`file://`) deixa header e footer em branco — isso é esperado.
Para testar localmente, rode um servidor:

```bash
npx serve .
```

Na Vercel funciona normalmente.

## Checkout

Os botões de compra apontam para:

- 530: `https://pagamento.santinsimports.com/checkout?product=aee90aad-9db4-11f1-a1eb-46da4690ad53`
- 9060: `https://pagamento.santinsimports.com/checkout?product=8369fe30-9db4-11f1-a1eb-46da4690ad53`
- Crocs: `https://pagamento.santinsimports.com/checkout?product=92fc7717-a012-11f1-a1eb-46da4690ad53`
- SmartWatch Preto: `https://pagamento.santinsimports.com/checkout?product=d5017075-a012-11f1-a1eb-46da4690ad53`
- SmartWatch Titanium: `https://pagamento.santinsimports.com/checkout?product=3a830e39-a013-11f1-a1eb-46da4690ad53`

## Conteúdo a revisar antes de publicar

Campos marcados com `[EDITÁVEL]` ou `[Informe aqui...]`:

- Tabela de conversão de tamanhos (BR / US / EU / CM) nas páginas de produto
- Prazos de processamento, entrega e frete (`entrega.html`)
- Condições de parcelamento sem juros (`pagamento.html`)
- Política de trocas e prazos (`trocas.html`)
- Endereço da razão social (`termos.html`, `privacidade.html`)
- Textos das avaliações de clientes (são modelos)


## Dependência externa

`support.js` carrega React 18.3.1, ReactDOM e Babel Standalone do CDN unpkg.com em
tempo de execução. O site só monta com internet e com o unpkg acessível. Se algum dia
o unpkg cair, as páginas ficam em branco.

## GitHub Pages

O arquivo `.nojekyll` na raiz é obrigatório. Sem ele, o GitHub processa os `{{ }}`
das páginas como template Liquid e apaga o conteúdo antes do navegador receber.
