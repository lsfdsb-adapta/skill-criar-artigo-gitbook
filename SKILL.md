---
name: criar-artigo-gitbook
description: Cria um artigo em Markdown no formato GitBook pronto para importação, com estrutura padrão e opcionalmente um GIF demonstrativo capturado de um fluxo real no browser, e explica onde os artefatos estão disponíveis no chat e no workspace. Use quando o usuário pedir um artigo GitBook, documentação de passo a passo de plataforma, ou material de documentação com GIF.
---

# Criar Artigo GitBook

## Missão
Criar um artigo em Markdown no formato de importação do GitBook, com estrutura padrão e (opcional) GIF demonstrativo, e entregar o outcome em locais claros para o usuário.

## Quando usar
- Usuário pede "artigo GitBook", "documentação", "passo a passo para publicar", ou "quero ver como fica no GitBook".
- Quando for preciso capturar um fluxo da plataforma e embutir como GIF no artigo.

## Fluxo de execução

1. **Identificar o tema e conteúdo do artigo**
   - Pergunte ao usuário o assunto, a audiência e o objetivo do artigo.
   - Reúna as informações necessárias: etapas, pré-requisitos, erros comuns, próximos passos.

2. **Estruturar o Markdown no padrão GitBook**
   - Um único `# Título` no topo.
   - Seções: `Visão geral`, `Pré-requisitos`, `Passo a passo` (cada passo com `Resultado esperado`), `Erros comuns` (tabela), `Próximos passos`.
   - Use blocos de dica: `{% hint style="info" %}` ... `{% endhint %}`.
   - Escreva em português claro e objetivo.

3. **Gerar GIF demonstrativo (opcional, mas recomendado quando houver fluxo de tela)**
   - Use a skill `adapta-studio` para gravar o fluxo no browser do sandbox Vercel.
   - Alternativamente, use `ffmpeg` para converter um vídeo existente em GIF, com tamanho/limites (< 200 frames, < ~1MB).
   - Salve o GIF em `artifacts/<slug-do-artigo>/.gitbook/assets/`.
   - Referencie o GIF no Markdown com: `![Descrição do GIF](.gitbook/assets/<arquivo>.gif)`.

4. **Montar a pasta de importação**
   - Crie a pasta `artifacts/<slug-do-artigo>/`.
   - Coloque o arquivo `<slug>.md` na raiz dessa pasta.
   - Coloque o GIF em `.gitbook/assets/` dentro da mesma pasta (caminho que o GitBook espera).

5. **Entregar e explicar onde estão os artefatos**
   - Informe ao usuário os 3 locais:
     1. O artigo completo: link do artifact (ex.: `artifact:<id>.md`).
     2. O GIF em movimento: `artifacts/<slug>/.gitbook/assets/<arquivo>.gif`.
     3. A pasta pronta para importação: `artifacts/<slug>/` com o `.md` e `.gitbook/assets/`, que pode ser importada no GitBook (via upload ou Git Sync).

## Regras
- Não publique nada sem revisão humana.
- Não invente fatos: use apenas informações confirmadas ou marcadas como hipótese.
- O GIF deve ser real (capturado), nunca editado de forma a distorcer o fluxo.
- Se algo não for capturável, explique a limitação e não simule.
