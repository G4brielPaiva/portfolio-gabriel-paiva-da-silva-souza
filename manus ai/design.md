# Design de Interface - Jitsi Meeting Manager

## Visão Geral

O aplicativo segue o padrão **Google Tasks** com uma interface limpa, minimalista e focada em produtividade. A orientação é **retrato móvel (9:16)** com suporte a uso com uma mão.

---

## Lista de Telas

1. **Home Screen** - Lista de reuniões agrupadas por data
2. **Meeting Detail** - Detalhes da reunião e opção de iniciar
3. **Create/Edit Meeting** - Formulário para criar ou editar reunião
4. **Settings** - Configurações do aplicativo

---

## Tela Principal: Lista de Reuniões

### Conteúdo Primário e Funcionalidade

**Estrutura da Tela:**
- **Header**: Título "Reuniões" com ícone de configurações
- **Search Bar**: Barra de busca com ícone de lupa (filtra por nome da reunião)
- **Color Filter**: Seletor de cores horizontal (filtra por categoria visual)
- **Meeting List**: Lista vertical agrupada por data com cabeçalhos de data

### Agrupamento por Data

As reuniões são organizadas em seções com cabeçalhos de data em ordem **decrescente** (próximas primeiro):
- **"Hoje"** - Reuniões de hoje
- **"Amanhã"** - Reuniões de amanhã
- **"15 de Maio"** - Data específica
- **"Próximas"** - Reuniões futuras agrupadas por semana

### Item de Reunião

Cada item exibe:
- **Borda colorida esquerda** (3-4px) com a cor hex definida pelo usuário
- **Título da reunião** (texto primário, bold)
- **Horário** (texto secundário, menor)
- **Status de conclusão** (ícone de checkbox opcional)
- **Ícone de ação** (seta para direita ou ícone de play para iniciar reunião)

### Interações

- **Tap no item**: Abre a tela de detalhes da reunião
- **Tap no ícone de play**: Abre a reunião Jitsi em WebView
- **Swipe para esquerda**: Opções de editar/deletar (opcional)
- **Tap no botão "+"**: Abre formulário de criar nova reunião

---

## Paleta de Cores

### Cores de Marca

| Token | Valor | Uso |
|-------|-------|-----|
| **Primary** | #0a7ea4 | Botões, ícones ativos |
| **Background** | #ffffff (light) / #151718 (dark) | Fundo da tela |
| **Surface** | #f5f5f5 (light) / #1e2022 (dark) | Cards, superfícies elevadas |
| **Foreground** | #11181C (light) / #ECEDEE (dark) | Texto primário |
| **Muted** | #687076 (light) / #9BA1A6 (dark) | Texto secundário |
| **Border** | #E5E7EB (light) / #334155 (dark) | Bordas, divisores |

### Cores de Categorias (Etiquetas de Reunião)

Paleta de 6 cores para categorias de reunião:
- **#4285F4** - Azul (padrão)
- **#EA4335** - Vermelho
- **#FBBC04** - Amarelo
- **#34A853** - Verde
- **#A142F4** - Roxo
- **#FF6D00** - Laranja

---

## Fluxos de Usuário Principais

### Fluxo 1: Visualizar Reuniões
1. Usuário abre o app → Home Screen
2. Lista de reuniões agrupadas por data é exibida
3. Usuário pode rolar para ver mais reuniões

### Fluxo 2: Buscar Reunião
1. Usuário toca na barra de busca
2. Digita o nome da reunião
3. Lista é filtrada em tempo real
4. Usuário toca no resultado para abrir detalhes

### Fluxo 3: Filtrar por Cor
1. Usuário toca em uma cor no seletor horizontal
2. Lista é filtrada para mostrar apenas reuniões dessa cor
3. Usuário pode desselecionar a cor para limpar o filtro

### Fluxo 4: Iniciar Reunião
1. Usuário toca no item de reunião ou no ícone de play
2. WebView abre com a URL Jitsi (https://meet.jit.si/[slug])
3. Usuário participa da videoconferência

### Fluxo 5: Criar Reunião
1. Usuário toca no botão "+" no header
2. Formulário abre com campos: título, data/hora, cor
3. Usuário preenche e toca "Salvar"
4. Reunião é adicionada à lista

---

## Tipografia e Espaçamento

### Tipografia

- **Títulos (H1)**: 24px, bold, foreground
- **Subtítulos (H2)**: 18px, semibold, foreground
- **Corpo (Body)**: 16px, regular, foreground
- **Secundário (Small)**: 14px, regular, muted
- **Micro**: 12px, regular, muted

### Espaçamento

- **Padding padrão**: 16px
- **Gap entre itens**: 12px
- **Raio de borda**: 8px-12px
- **Altura de item**: 64px-72px

---

## Sombras e Elevação

- **Sem sombra**: Fundo, texto
- **Sombra suave**: Cards, superfícies elevadas (0 2px 8px rgba(0,0,0,0.1))
- **Sombra média**: Modais, sheets (0 4px 16px rgba(0,0,0,0.15))

---

## Feedback Visual

- **Press State**: Opacidade 0.7 em items
- **Haptic Feedback**: Leve ao tocar em botões primários
- **Loading**: Spinner ou skeleton loading
- **Success**: Ícone de checkmark com cor success (#22C55E)

---

## Acessibilidade

- Contraste mínimo de 4.5:1 para texto
- Tamanho mínimo de toque: 44x44px
- Labels descritivos para ícones
- Suporte a modo escuro automático
