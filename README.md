# Contagem e Frangos

App web instalável (PWA) para usar no celular. Funciona sem internet depois da primeira visita e não precisa de servidor: é só abrir o endereço do GitHub Pages.

## Abas

- **Contagem**: estoque por categoria ou por fornecedor, seção de Produtos de Giro Rápido, observação e campo "Comprar" em cada item, relatório na tela, em PDF, em planilha (CSV) e em texto para WhatsApp.
- **Frangos**: valores por dia da semana (terça a domingo), total e texto pronto para copiar.
- **Backup**: exportar e importar todos os dados (arquivo `.json` ou texto).

## Arquivos

Todos ficam na mesma pasta, sem subpastas:

| Arquivo | Para que serve |
| --- | --- |
| `index.html` | O app inteiro |
| `manifest.webmanifest` | Nome, cores e ícones do app instalado |
| `sw.js` | Faz o app abrir sem internet |
| `icon-192.png`, `icon-512.png` | Ícones do app |
| `icon-maskable-512.png` | Ícone adaptável do Android |
| `apple-touch-icon.png` | Ícone do iPhone |

## Publicar no GitHub Pages

1. Crie um repositório novo no GitHub (por exemplo, `estoque`).
2. Envie os 7 arquivos para a raiz do repositório (botão **Add file > Upload files**) e confirme o commit.
3. Vá em **Settings > Pages**. Em **Build and deployment**, escolha **Deploy from a branch**, selecione a branch `main` e a pasta `/ (root)`, e salve.
4. Espere cerca de um minuto. O endereço aparece na mesma tela, no formato `https://SEU-USUARIO.github.io/estoque/`.

Também funciona dentro de uma pasta de outro repositório, porque todos os caminhos são relativos.

## Instalar no celular

- **Android (Chrome)**: abra o endereço e toque em **Instalar app**, que aparece na aba Backup. Se o botão não aparecer, use o menu do navegador e toque em **Instalar app** ou **Adicionar à tela inicial**.
- **iPhone (Safari)**: abra o endereço, toque em **Compartilhar** e depois em **Adicionar à Tela de Início**.

Depois de instalado, o app abre em tela cheia, como qualquer outro.

## Onde ficam os dados

Os dados ficam **só no navegador do aparelho** em que você usa o app. Não há sincronização entre aparelhos.

- Limpar os dados do navegador apaga tudo.
- O endereço faz parte do armazenamento: se você mudar o nome do repositório ou usar outro domínio, o app abre vazio. Faça um backup antes de mudar.
- O app instalado e a página aberta no navegador podem guardar dados separados no mesmo aparelho. Escolha um dos dois para o uso diário.

## Backup

Na aba **Backup**:

- **Baixar arquivo**: gera `backup-estoque-AAAA-MM-DD.json`.
- **Compartilhar arquivo**: aparece quando o aparelho permite. Útil no iPhone, para salvar em Arquivos ou enviar pelo WhatsApp.
- **Copiar como texto**: copia o backup para colar em outro aparelho.
- **Importar**: escolha o arquivo ou cole o texto, confira o resumo e escolha:
  - **Substituir tudo**: apaga o que está no aparelho e usa só o backup.
  - **Mesclar**: junta o backup com o que já existe. Itens cadastrados à mão nos dois aparelhos podem ficar duplicados.
- **Desfazer última importação**: volta ao que existia antes da importação.

O backup inclui a contagem, as categorias, os fornecedores, os produtos de giro rápido e os valores dos Frangos. A aba avisa quando o último backup tem 7 dias ou mais. Um bom hábito é fazer um backup toda semana, junto com a contagem.

### Levar os dados do link do Claude para o GitHub Pages

1. No link antigo (o do Claude), abra a aba Backup e toque em **Copiar como texto**.
2. No app do GitHub Pages, abra a aba Backup, cole o texto na caixa, toque em **Ler texto colado** e depois em **Substituir e importar**.

## Atualizar o app

- Para mudar o app, substitua só o `index.html` no repositório. Na próxima vez que o app abrir com internet, ele já pega a versão nova.
- Se mudar os ícones ou o manifesto, aumente o número da versão em `sw.js` (por exemplo, de `estoque-v1` para `estoque-v2`).

## Problemas comuns

- **A página dá erro 404**: confirme que os arquivos estão na raiz da branch escolhida e espere um ou dois minutos depois de ativar o Pages.
- **Só consigo criar atalho, ou aparece "Não foi possível abrir o aplicativo"**:
  1. Abra no navegador `SEU-ENDERECO/manifest.webmanifest` e `SEU-ENDERECO/sw.js`. Os dois precisam mostrar texto. Se der 404, falta enviar o arquivo ou ele está na pasta errada.
  2. Apague da tela inicial qualquer atalho criado antes.
  3. Abra o endereço no Chrome, espere carregar, feche a aba e abra de novo, para o app atualizar.
  4. Toque nos três pontinhos e escolha **Instalar app**. Se o menu mostrar **Abrir app**, o Chrome acha que o app já está instalado. Nesse caso, digite `chrome://webapks` na barra de endereço para ver os apps instalados e remova o que for desta página.
- **O botão Instalar não aparece**: o app precisa estar aberto pelo endereço `https://` do GitHub Pages, e talvez já esteja instalado. No iPhone não existe esse botão, use Compartilhar.
- **O download do arquivo não funciona no iPhone**: use **Compartilhar arquivo** ou **Copiar como texto**.
- **Os dados sumiram**: provavelmente os dados do navegador foram limpos ou o endereço mudou. Importe o último backup.
- **O app não mostra a versão nova**: feche o app por completo e abra de novo com internet.
