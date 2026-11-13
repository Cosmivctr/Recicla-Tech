# ReciclaTech ♻️💻

Site institucional de uma **ONG fictícia** que recolhe computadores parados, recupera os equipamentos, instala recursos de acessibilidade e doa para escolas públicas, para estudantes com deficiência.

Projeto acadêmico da **Atividade A2** da disciplina de **Front-End** da **UNICID** (Universidade Cidade de São Paulo), 2026.

> ⚠️ A ReciclaTech é uma organização fictícia. Números, depoimentos, dados de contato, chave PIX e instruções de pagamento são **ilustrativos**. Nenhuma doação ou cobrança real é feita pelo site.

---

## Sumário

- [Sobre o projeto](#sobre-o-projeto)
- [Páginas](#páginas)
- [Acessibilidade](#acessibilidade)
- [Tecnologias](#tecnologias)
- [Estrutura de pastas](#estrutura-de-pastas)
- [Como executar](#como-executar)
- [Doação em dinheiro (EmailJS)](#doação-em-dinheiro-emailjs)
- [Dados salvos no navegador](#dados-salvos-no-navegador)
- [Validação e testes](#validação-e-testes)
- [Equipe](#equipe)
- [Créditos](#créditos)

---

## Sobre o projeto

A ideia une dois problemas: muitas pessoas com deficiência não têm acesso a um computador preparado para elas, e toneladas de eletrônicos que ainda funcionam são descartadas todos os anos. O site apresenta a ONG, mostra o impacto do trabalho e permite doar equipamentos, se voluntariar ou fazer uma doação em dinheiro.

Como o tema é inclusão, o site foi pensado **acessível desde o início**: navegação completa pelo teclado, alto contraste, ajuste do tamanho da fonte, leitura em voz alta e compatibilidade com leitores de tela.

## Páginas

| Página | Conteúdo |
|---|---|
| `index.html` | Página inicial: chamada principal, os 5 passos do processo, números de impacto e convite para participar |
| `sobre.html` | História, missão, visão e valores |
| `projetos.html` | Os projetos da ONG, o ciclo "do descarte à sala de aula", vantagens de doar e funções de voluntariado |
| `impacto.html` | Tabelas de resultados e depoimentos |
| `acessibilidade.html` | Recursos instalados nos computadores, recursos do site e atalhos de teclado |
| `galeria.html` | Galeria de imagens com visualização ampliada |
| `midia.html` | Vídeo com legendas, podcast com transcrição e mapa dos pontos de coleta |
| `noticias.html` | Notícias sobre tecnologia assistiva, inclusão e descarte correto |
| `contato.html` | Formulário de contato, formulário de doação em dinheiro e equipe do projeto |
| `orcamento-hospedagem.html` | Comparação de hospedagens e domínios para publicar o site |

## Acessibilidade

Recursos disponíveis em **todas as páginas**:

- **Alto contraste**: fundo preto, texto branco e destaques em amarelo. A escolha fica salva no navegador.
- **Tamanho da fonte (A-, A, A+)**: de 80% a 130%. Como o CSS usa `rem`, o site inteiro acompanha.
- **Leitura em voz alta**: lê o conteúdo da página com a Web Speech API do navegador, começando pelo texto selecionado ou pelo trecho visível. O trecho lido fica destacado, e dá para pausar, parar e ajustar a velocidade.
- **Link "Pular para o conteúdo principal"**: aparece ao navegar com a tecla Tab.
- **Navegação completa pelo teclado**, com foco sempre visível.
- **HTML semântico**: `header`, `nav`, `main`, `section`, `article`, `aside`, `footer`, `figure`/`figcaption`, hierarquia de títulos correta e tabelas com `caption` e `th`.
- **ARIA usado só quando necessário**: `aria-current` no link da página atual, `aria-expanded` no menu, `aria-pressed` no botão de alto contraste, `aria-invalid` e `aria-describedby` nos campos com erro, e mensagens com `role="status"` e `role="alert"`.
- **Formulários acessíveis**: todo campo tem `<label>`, os grupos de opções usam `fieldset`/`legend`, os erros aparecem em texto (não só em cor) e o foco vai para o primeiro campo com erro.
- **Contraste mínimo AA (WCAG 2.1)**, conferido nos modos normal e de alto contraste.
- **Fonte Atkinson Hyperlegible**, criada para facilitar a leitura de pessoas com baixa visão.
- **Alvos de toque grandes** (mínimo de 48px) para quem usa o celular.

## Tecnologias

- **HTML5**
- **CSS3**: variáveis CSS, `@layer`, Grid, Flexbox, `:has()`, `:where()`, `color-mix()` e cores em `oklch()`. As classes utilitárias vieram do Tailwind CSS e estão escritas direto no `style.css`, sem nenhuma etapa de build.
- **JavaScript puro** (sem frameworks).
- **[EmailJS](https://www.emailjs.com)**: envio do e-mail de confirmação da doação, direto do navegador.
- **Web Speech API**: leitura em voz alta.
- **localStorage**: guarda as preferências e o rascunho da doação.

O site é **estático**: não tem back-end nem banco de dados.

## Estrutura de pastas

```
reciclatech/
├── index.html
├── sobre.html
├── projetos.html
├── impacto.html
├── acessibilidade.html
├── galeria.html
├── midia.html
├── noticias.html
├── contato.html
├── orcamento-hospedagem.html
├── style.css             # todo o CSS do site, em 11 seções comentadas
├── script.js             # alto contraste, menu, painel de ajustes e formulário de contato
├── tamanho.js            # botões A-, A, A+
├── leitura-voz.js        # leitura em voz alta
├── galeria.js            # janela da imagem ampliada (galeria.html)
├── doacao.js             # formulário de doação em dinheiro (contato.html)
├── LEIA-ME-doacao.md     # configuração do EmailJS e checklist de testes da doação
├── files/
│   └── preview.webp      # foto do topo da página inicial
└── media/
    ├── video.mp4         # vídeo da página Mídia
    ├── legendas.vtt      # legendas do vídeo
    └── podcast.mp3       # episódio do podcast
```

Todos os arquivos `.js` ficam dentro de uma função que se executa sozinha, com `"use strict"`, e seguem a mesma ordem: configuração → referências aos elementos → funções → eventos → início.

## Como executar

Como o site é estático, não precisa instalar nada.

1. Clone o repositório:
   ```bash
   git clone <endereço-do-repositório>
   ```
2. Abra a pasta no **VS Code** e inicie a extensão **Live Server** (clique com o botão direito em `index.html` > *Open with Live Server*).

> Prefira abrir pelo Live Server (ou outro servidor local) em vez de dar duplo clique no arquivo. Assim o envio de e-mail da doação e o `localStorage` funcionam como no site publicado.

## Doação em dinheiro (EmailJS)

O formulário de doação (`contato.html`) valida os campos, guarda um rascunho enquanto a pessoa preenche e envia um **e-mail de confirmação** para o doador pelo EmailJS.

As chaves ficam no topo do `doacao.js`:

```js
const PUBLIC_KEY = "...";
const SERVICE_ID = "...";
const TEMPLATE_ID = "...";
```

O passo a passo para criar a conta, o serviço e o template do e-mail, com o texto do template e o checklist de testes, está em **[LEIA-ME-doacao.md](LEIA-ME-doacao.md)**.

> A *Public Key* do EmailJS foi feita para ficar no código do site. **Nunca** coloque no repositório a *Private Key* nem a senha do e-mail.

## Dados salvos no navegador

| Chave do `localStorage` | Para que serve |
|---|---|
| `rt-hc` | Lembra se o alto contraste está ligado |
| `rt-fs` | Lembra o tamanho da fonte escolhido |
| `rt-doacao-rascunho` | Rascunho do formulário de doação (apagado ao enviar ou ao clicar em "Limpar") |
| `rt-doacao-ultima` | Data da última doação enviada |

O formulário de contato não guarda nada. O `script.js` ainda apaga o rascunho antigo `rt-contato`, de uma versão anterior do site.

## Validação e testes

- **HTML** validado no [W3C Nu HTML Checker](https://validator.w3.org/nu/).
- **CSS** validado no [W3C CSS Validator](https://jigsaw.w3.org/css-validator/).
- Funcionamento testado nas 10 páginas: sem erros no console, no computador e no celular, nos modos normal e de alto contraste.
- O formulário de doação tem um checklist de testes no [LEIA-ME-doacao.md](LEIA-ME-doacao.md), com campos vazios, e-mail inválido, envio com sucesso, atualização da página no meio do preenchimento, "Limpar" e modo offline.

## Equipe

| Integrante | Responsabilidade |
|---|---|
| Allex Felix Lemos Viana | Página inicial, modelo base e CSS |
| Arthur Ferreira Magalhães | Sobre e Projetos, identidade visual |
| Felipe Rocha Torres | Impacto e Notícias, pesquisa de dados |
| Henrique Vieira de Souza | Acessibilidade, testes de acessibilidade |
| Mateus de Santana Faria | Galeria e Mídia, imagens, vídeo e áudio |
| João Victor Ferreira Cosmi | Contato e Orçamento, formulário |

## Créditos

- Fonte [Atkinson Hyperlegible](https://fonts.google.com/specimen/Atkinson+Hyperlegible), do Braille Institute, via Google Fonts.
- Ícones no estilo [Lucide](https://lucide.dev).
- Imagens da galeria geradas por IA (Google Gemini), como indicado em cada legenda.
- Classes utilitárias baseadas no [Tailwind CSS](https://tailwindcss.com).

---

Projeto acadêmico, sem fins comerciais. © 2026 Equipe ReciclaTech, UNICID.
