# Portal Integra SGE

## Descrição

Portal da Gerência de Sistematização e Gerenciamento Escolar (GSGE) da SEDUC-TO para receber as planilhas de estudantes da Transferência de Alunos (TA) enviadas pelos municípios.

Funciona como um Google Forms: o remetente informa **Nome, Instituição, Telefone, E-mail, Assunto e Descrição** e anexa as planilhas.

## Arquitetura

- **frontend/**: aplicação web (formulário de envio), publicada no Vercel (plano gratuito).
- **apps-script/**: Google Apps Script publicado como App da Web. Ao receber um envio, ele:
  1. salva as planilhas numa pasta do Google Drive, em subpastas por mês (`AAAA-MM`);
  2. registra uma linha na planilha Google "Registro de Envios";
  3. envia e-mail para a gerência com as planilhas **anexadas**;
  4. envia e-mail de confirmação (sem anexo) para o remetente.
- **docs/**: documentação do projeto.

## Stack

- Frontend: React + Vite + TypeScript + Tailwind CSS
- Backend: Google Apps Script (App da Web), Google Drive e Google Sheets
- Deploy do frontend: Vercel

## Estrutura de pastas

```
portal-integra-sge/
├── apps-script/   # código do Google Apps Script
├── docs/          # documentação
├── frontend/      # criado pelo Vite no Sprint 2 (ainda não existe)
├── .gitignore
├── CLAUDE.md
└── README.md
```

## Formatos e limites

- Formatos aceitos: `.xlsx`, `.xls`, `.xlsm`, `.csv`, `.ods`
- De 1 a 5 arquivos por envio
- Até 10 MB por arquivo e 15 MB no total
- Cada envio gera um protocolo no formato `TA-AAAAMMDD-NNNN`

## Regras permanentes

- Textos da interface e comentários em português do Brasil; nomes de variáveis e funções em inglês.
- Nunca commitar credenciais, IDs reais de pasta ou planilha, e-mails reais, arquivos `.env` ou planilhas.
- IDs e e-mails ficam nas Propriedades do Script (Apps Script) e nas variáveis de ambiente (Vercel).
- Validar formato e tamanho dos arquivos no frontend **e** no backend.
- Interface acessível, responsiva e em português.
- Sempre entregar arquivos completos e explicar as mudanças para um iniciante.

## LGPD

As planilhas contêm dados pessoais de estudantes, muitos menores de idade. O repositório no GitHub é **público**: nenhum dado real pode ir para ele, nem em exemplos, testes ou logs.
