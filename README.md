<div align="center">

<img src="Logomarca.PNG" alt="Flow Board" width="180"/>

# Flow Board

### Kanban de Projetos — Zero dependências, deploy em um arquivo

<br/>

[![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/HTML)
[![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/CSS)
[![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
[![License: MIT](https://img.shields.io/badge/License-MIT-22c55e?style=for-the-badge)](LICENSE)

[![Single File](https://img.shields.io/badge/deploy-single%20file-8b5cf6?style=flat-square)](index.html)
[![No Build](https://img.shields.io/badge/build-none%20required-0ea5e9?style=flat-square)](#instalação)
[![No Dependencies](https://img.shields.io/badge/dependencies-0-22c55e?style=flat-square)](#stack-técnica)
[![SharePoint Ready](https://img.shields.io/badge/SharePoint-ready-0078d4?style=flat-square&logo=microsoftsharepoint&logoColor=white)](#opção-2--integração-com-sharepoint)

<br/>

> **Um único arquivo HTML** que entrega um sistema Kanban completo — com múltiplos usuários, 8 temas visuais, calendário, Gantt, dashboard de KPIs, rastreamento de ganhos e suporte a SharePoint. Sem npm. Sem servidor. Sem configuração.

</div>

---

## ✨ O que ele faz

<table>
<tr>
<td width="50%">

**📋 Gestão de projetos**
- Quadro Kanban com colunas customizáveis
- Drag-and-drop de cards entre colunas
- Limites WIP por coluna
- Filtros, busca e ordenação
- Subtarefas, dependências e histórico

</td>
<td width="50%">

**👥 Colaboração em equipe**
- Múltiplos usuários simultâneos
- Lock otimista anti-conflito
- Comentários por card
- Notificações em tempo real (polling)
- Responsáveis, solicitantes e helpers

</td>
</tr>
<tr>
<td width="50%">

**📊 Visualizações**
- Quadro Kanban
- Dashboard com KPIs e gráficos
- Calendário mensal de entregas
- Gantt com linha do tempo
- Log de atividade e cards arquivados

</td>
<td width="50%">

**💰 Rastreamento de ganhos**
- Horas/mês e horas/ano (auto ×12)
- Economia financeira mensal e anual
- Tags qualitativas por card
- Painel consolidado no dashboard
- Gráfico de barras por projeto

</td>
</tr>
<tr>
<td width="50%">

**🎨 Experiência visual**
- 8 temas: 4 claros + 4 escuros
- Design responsivo
- Modo escuro automático (segue o SO)
- Acessibilidade WCAG AA

</td>
<td width="50%">

**⚡ Infraestrutura simples**
- Zero dependências externas
- File System Access API (edição local)
- Cache offline automático
- Exportação CSV e PDF
- Integração opcional com SharePoint

</td>
</tr>
</table>

---

## 🏗️ Stack Técnica

| Camada | Tecnologia |
|---|---|
| Interface | HTML5 semântico + CSS3 (Grid, Flexbox, variáveis customizadas) |
| Lógica | JavaScript ES2020 vanilla (sem frameworks) |
| Persistência local | [File System Access API](https://developer.mozilla.org/en-US/docs/Web/API/File_System_Access_API) + `localStorage` |
| Persistência remota | Microsoft SharePoint (fetch relativo ou URL absoluta) |
| Formato de dados | JSON (`data.json`) — leitura/escrita direta no sistema de arquivos |
| Deploy | Um único `index.html` — sem build, sem servidor, sem CDN |

---

## 📋 Pré-requisitos

| Requisito | Detalhes |
|---|---|
| **Modo edição** | Google Chrome 86+ ou Microsoft Edge 86+ |
| **Modo leitura** | Qualquer navegador moderno |
| **Servidor** | Nenhum — funciona com `file://` diretamente |
| **Node / npm** | Não necessário |
| **SharePoint** | Opcional — para uso compartilhado em equipe |

---

## 🚀 Instalação

### Opção 1 — Local (mais simples)

```bash
git clone https://github.com/seu-usuario/flow-board.git
cd flow-board
```

1. Abra `index.html` no **Chrome** ou **Edge**
2. Na tela de setup, selecione a **pasta** onde está o `data.json`
3. Informe seu **nome** (o ID de dispositivo é gerado automaticamente)
4. Escolha o modo **Edição** e clique em **Entrar no quadro**

> **Nota:** O navegador solicitará permissão de acesso à pasta a cada sessão — comportamento padrão de segurança do browser.

---

### Opção 2 — Integração com SharePoint

1. Faça upload de `index.html` e `data.json` para uma biblioteca de documentos do SharePoint
2. Edite as duas constantes no final de `index.html`:

```javascript
// Busca relativa — funciona quando index.html está na mesma pasta do data.json
// './data.json' já configurado por padrão — nenhuma alteração necessária

// URL absoluta de fallback (substitua pelos valores do seu tenant)
const SHAREPOINT_DATA_URL_ABS    = 'https://YOUR-COMPANY.sharepoint.com/teams/YOUR-TEAM/Shared%20Documents/kanban/data.json';
const SHAREPOINT_DATA_URL_DIRECT = 'https://YOUR-COMPANY.sharepoint.com/teams/YOUR-TEAM/_layouts/15/download.aspx?UniqueId=YOUR-FILE-UNIQUE-ID';
```

3. Acesse `index.html` via URL do SharePoint — o `data.json` é carregado automaticamente

---

### Opção 3 — Servidor HTTP estático

```bash
# Python 3
python -m http.server 8080

# Node.js
npx serve .

# Live Server (VS Code)
# Clique em "Go Live" na barra inferior
```

Acesse `http://localhost:8080`.

---

## 🔐 Sistema de Usuários

O Flow Board usa um sistema de identificação **sem cadastro e sem senha**:

| Situação | Comportamento |
|---|---|
| **Primeiro acesso** | Um ID único é gerado automaticamente para o dispositivo. Você informa apenas seu nome. |
| **Acessos seguintes (mesmo navegador)** | Login automático — sem interação manual. |
| **Novo navegador / dispositivo** | Informe seu nome + o ID copiado do dispositivo anterior para manter o mesmo perfil. |
| **ID desconhecido** | Um novo perfil é criado automaticamente. |

> O ID do dispositivo pode ser copiado na tela de setup e usado em outros navegadores para manter continuidade de perfil.

---

## 📁 Estrutura de Arquivos

```
flow-board/
│
├── index.html        ← Aplicação completa (HTML + CSS + JS, ~425 KB)
├── data.json         ← Banco de dados (cards, colunas, usuários, notificações)
├── Logomarca.PNG     ← Logo exibido na barra lateral e tela de setup
├── icon.PNG          ← Ícone da aba do navegador (favicon)
└── README.md         ← Esta documentação
```

---

## ⚙️ Estrutura do `data.json`

```json
{
  "revision": 1,
  "lastModified": "2026-01-01T00:00:00.000Z",
  "lastModifiedBy": "Sistema",
  "lastModifiedByUserId": "",
  "users": {},
  "columns": [
    { "id": "backlog",   "name": "Backlog",      "wipLimit": null },
    { "id": "andamento", "name": "Em Andamento", "wipLimit": null },
    { "id": "pausa",     "name": "Em Pausa",     "wipLimit": null },
    { "id": "concluido", "name": "Concluído",    "wipLimit": null }
  ],
  "cards": [],
  "historyMonth": "2026-01",
  "notifications": []
}
```

| Campo | Descrição |
|---|---|
| `revision` | Contador automático para detecção de conflito entre usuários |
| `users` | Registro `{ "deviceId": "Nome" }` — populado no primeiro login |
| `columns` | Colunas do quadro — editáveis pela interface |
| `cards` | Todos os cards (ativos e arquivados) |
| `historyMonth` | Mês de referência para limpeza automática do histórico |

---

## 🎨 Temas Disponíveis

| # | Nome | Tipo | Característica |
|---|---|---|---|
| 1 | Padrão | ☀️ Claro | Verde e amarelo — tema principal |
| 2 | Sage | ☀️ Claro | Verde musgo e esmeralda |
| 3 | Dusk | ☀️ Claro | Lavanda e violeta |
| 4 | Sand | ☀️ Claro | Terroso e âmbar |
| 5 | Dark | 🌙 Escuro | Cinza escuro neutro |
| 6 | Dracula | 🌙 Escuro | Inspirado no tema Dracula |
| 7 | Cyberpunk | 🌙 Escuro | Neon e alto contraste |
| 8 | Really Dark | 🌙 Escuro | Preto profundo |

Selecionável pelo ícone 🎨 na barra lateral. Preferência salva automaticamente.

---

## 🤝 Contribuindo

```bash
# 1. Fork e clone
git clone https://github.com/seu-usuario/flow-board.git

# 2. Crie uma branch
git checkout -b feature/minha-melhoria

# 3. Edite index.html diretamente — sem build necessário
# Navegue pelas seções com /* ===...=== */ como marcadores

# 4. Teste no Chrome e Edge (modo edição e leitura)

# 5. Commit e PR
git commit -m "feat: descrição da melhoria"
git push origin feature/minha-melhoria
```

**Dicas:**
- Toda a aplicação está em `index.html` — use `Ctrl+F` para navegar
- Seções são delimitadas por blocos de comentário `/* ===...=== */`
- Sem processo de build — edite e abra no navegador diretamente

---

## 📄 Licença

Distribuído sob a [MIT License](LICENSE). Uso livre para projetos pessoais e comerciais.

---

<div align="center">

**Flow Board** · Kanban simples, poderoso e sem dependências

*Feito com HTML, CSS e JavaScript puro.*

</div>
