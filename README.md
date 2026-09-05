# 🎮 Catch Buddies 👋

![Logo Catch Buddies](assets/logo/logo.png)

> **Aplicativo social leve e gamificado para explorar, conectar e iniciar novas amizades.**  
> Protótipo Front-End de Alta Fidelidade (Mobile-First) desenvolvido com JavaScript Vanilla, CSS3 modular e arquitetura orientada a serviços para futura integração com backend PHP e banco de dados MySQL.

---

## 📌 Objetivo Desta Versão

Validar de ponta a ponta a ideia central do aplicativo através do ciclo essencial:
$$\text{DESCOBRIR} \longrightarrow \text{CAPTURAR} \longrightarrow \text{ACEITAR} \longrightarrow \text{CONECTAR} \longrightarrow \text{CONVERSAR}$$

O projeto foca na experiência essencial do usuário, sem distrações com funcionalidades secundárias (como rankings, níveis ou feeds), garantindo consistência visual, usabilidade mobile-first e regras de negócio sólidas.

---

## 🛠️ Tecnologias Utilizadas

- **HTML5 Semântico**: Estrutura acessível com tags semânticas (`<header>`, `<main>`, `<nav>`, `<section>`, `<article>`), sem `onclick` ou estilos inline.
- **CSS3 Moderno & Modular**:
  - CSS Variables / Design Tokens (`variables.css`);
  - Layout com Flexbox e CSS Grid (`global.css`);
  - Componentes reutilizáveis com efeito glassmorphism e iluminação glow neon (`components.css`);
  - Responsividade e acessibilidade (`responsive.css`).
- **JavaScript Puro (ES6+ Modules)**:
  - Arquitetura SPA (Single-Page Application) fluida sem frameworks pesados;
  - Estado centralizado e reativo (`state.js`);
  - Camada de serviços desacoplada com Promises e `async/await` (`services/`);
  - Notificações visuais acessíveis (Toasts sem uso de `window.alert()`).
- **Recursos Visuais**:
  - Logotipo oficial do Catch Buddies preservado (`assets/logo/logo.png`);
  - Avatares ilustrados em SVG de alta fidelidade e visual consistente (`assets/avatars/`).

---

## 📁 Estrutura de Pastas

```text
ProjectFatec-P.I-main/
│
├── index.html                   # Ponto de entrada principal da aplicação (SPA)
│
├── css/
│   ├── variables.css            # Tokens de cores, fontes, gradientes, bordas e sombras
│   ├── reset.css                # Normalização e reset CSS
│   ├── global.css               # Estrutura base, moldura mobile e barra inferior
│   ├── components.css           # Radar, cards de buddies, abas, chat, modais e toasts
│   └── responsive.css           # Ajustes para mobile compacto, tablets, desktop e acessibilidade
│
├── js/
│   ├── app.js                   # Controlador principal, renderização e eventos
│   ├── state.js                 # Gerenciamento do estado centralizado e persistência
│   ├── navigation.js            # Controle de navegação entre as 4 áreas principais
│   │
│   ├── services/                # Camada de serviços assíncronos (Interface <-> Mock/API)
│   │   ├── buddyService.js      # Listagem de buddies e busca por ID
│   │   ├── captureService.js    # Envio, aceite, recusa e simulação de capturas
│   │   ├── friendshipService.js # Gestão de amizades e validação de vínculo
│   │   ├── chatService.js       # Mensagens, histórico e resposta simulada
│   │   └── profileService.js    # Perfil do usuário e atualização
│   │
│   ├── data/
│   │   └── mockData.js          # Dados simulados iniciais (usuário, buddies, conversas)
│   │
│   └── utils/
│       ├── storage.js           # Utilitário seguro para localStorage
│       └── notifications.js     # Componente de feedback visual Toast
│
├── assets/
│   ├── logo/
│   │   └── logo.png             # Logotipo oficial do projeto
│   └── avatars/                 # Avatares vetoriais estilizados (SVGs)
│
└── README.md                    # Documentação do projeto
```

---

## 🚀 Funcionalidades Implementadas

1. **Descobrir Buddies & Mapa Interativo**:
   - **Mapa Dark Matter com Leaflet**: Exibe a localização do usuário (Fatec Marília) e de todos os possíveis Buddies ao redor;
   - **Pins Personalizados**: Marcadores no mapa com foto/avatar de cada pessoa, dot de status online e etiqueta de distância em metros;
   - **Raio de Captura (100m)**: Zona circular pulsante ao redor do usuário indicando o alcance ativo de captura;
   - **Mecânica "Ir até o Buddy" (Caminhar até aqui)**: Para buddies distantes, o usuário pode clicar em *"Ir até o Buddy"*; o mapa anima o trajeto em tempo real, recalculando a distância até entrar na zona de alcance e desbloquear o botão **"⚡ Capturar Buddy"**;
   - **Controles de Mapa**: Botões rápidos para centralizar no usuário e resetar a posição inicial para a Fatec;
   - **Lista Sincronizada**: Cards com distâncias dinâmicas e atalhos para focar ou caminhar até a pessoa.

2. **Perfil Resumido do Buddy (Modal)**:
   - Apresenta foto, nome, apelido, biografia, interesses e distância;
   - Botão dinâmico contextual para envio de captura com feedback visual.

3. **Solicitações de Captura (Abas Recebidas e Enviadas)**:
   - **Recebidas**: Apresenta solicitações pendentes de outros usuários, com botões **"Aceitar"** (cria amizade e libera o chat) e **"Recusar"** (não cria amizade e mantém bloqueado);
   - **Enviadas**: Apresenta capturas feitas pelo usuário (Pendente, Aceita, Recusada), com botões exclusivos para **Simular Aceite** ou **Simular Recusa** (recurso demonstrativo).

4. **Meus Buddies (Amizades Confirmadas)**:
   - Exibe exclusivamente pessoas com amizade aceita;
   - Status online/offline demonstrativo;
   - Prévia e horário da última mensagem;
   - Botão direto para iniciar a conversa.
   - Estado vazio convidativo com botão para ir até "Descobrir".

5. **Chat Individual Particular**:
   - **Bloqueio rígido**: só pode ser aberto caso haja amizade confirmada;
   - Histórico de mensagens com balões diferenciados para enviadas e recebidas;
   - Validação de mensagens vazias e rolagem automática;
   - Simulação de resposta amigável automática após 1,2 segundos.

6. **Perfil do Usuário & Restauração**:
   - Exibe informações do usuário principal fictício (**Mateus Yuri**);
   - Contadores de buddies, capturas enviadas e recebidas;
   - Edição de nome, apelido, bio e interesses com salvamento em `localStorage`;
   - Botão **"Restaurar Demonstração"** com confirmação de segurança para retornar os dados ao cenário inicial padrão.

---

## 🎯 Cenários de Demonstração

### Fluxo A: Enviar Captura para Alguém
1. Abra a aba **Descobrir**;
2. Escolha **Rafa Silveira** ou **Ana Clara** e clique em **"Capturar Buddy"** (ou abra o perfil e clique em capturar);
3. Veja a confirmação visual (Toast) e o botão mudando para *"Aguardando resposta"*;
4. Abra a aba **Capturas** e selecione a aba **Enviadas**;
5. Veja a captura com status **Pendente**;
6. Clique no botão de demonstração **"Simular aceite"**;
7. Abra a aba **Buddies**: o novo amigo agora aparece na sua lista;
8. Clique no ícone de conversa para abrir o **Chat** e envie uma mensagem.

### Fluxo B: Responder a uma Captura Recebida
1. Abra a aba **Capturas** e selecione a aba **Recebidas**;
2. Veja a solicitação enviada por **Lucas Fernandes**;
3. Clique em **"Aceitar"**;
4. Receba o feedback de que a conexão foi criada;
5. Vá para a aba **Buddies** e veja Lucas na sua lista;
6. Abra o chat com Lucas para conversar.

---

## 💾 Persistência de Dados (localStorage)

Os dados são armazenados de forma isolada na chave `CATCH_BUDDIES_DATA_V1`.
- **O que é persistido**: dados do perfil editado, capturas pendentes/aceitas/recusadas, lista de amigos confirmados e mensagens do chat.
- **Segurança**: não são salvos dados sensíveis, credenciais, e-mails reais ou senhas.
- **Restauração**: A qualquer momento, clique em **Perfil** $\rightarrow$ **Restaurar Demonstração** para resetar todo o estado para o cenário inicial.

---

## 🔌 Preparação para Futura Integração com PHP e MySQL

A aplicação foi desenvolvida seguindo o padrão de **Camada de Serviços (Service Layer)**. A interface (`app.js`) nunca acessa o `localStorage` nem dados brutos diretamente.

### Localização dos Serviços:
- `js/services/buddyService.js`
- `js/services/captureService.js`
- `js/services/friendshipService.js`
- `js/services/chatService.js`
- `js/services/profileService.js`

### Como Substituir Mocks por Endpoints PHP:

Todas as funções dos serviços já utilizam `async/await` e retornam `Promise`. Para conectar ao seu backend em PHP futuramente, basta trocar o corpo da função por uma requisição `fetch()`:

```javascript
// Exemplo em js/services/buddyService.js:

// HOJE (Dados Simulados):
export const buddyService = {
  async getNearbyBuddies() {
    return new Promise((resolve) => {
      resolve([...state.getBuddies()]);
    });
  }
};

// FUTURAMENTE (API PHP):
export const buddyService = {
  async getNearbyBuddies() {
    const response = await fetch('/api/buddies.php');
    if (!response.ok) throw new Error('Falha ao carregar buddies');
    return await response.json();
  }
};
```

Nenhuma linha de código dos componentes visuais precisará ser reescrita para a transição para PHP/MySQL.

---

## 💻 Como Executar o Projeto

Como a aplicação utiliza módulos ES6 nativos do JavaScript (`import`/`export`), recomenda-se executá-la através de um servidor web local:

### Opção 1: Extensão Live Server (VS Code)
1. Abra a pasta do projeto no VS Code;
2. Clique com o botão direito em `index.html` e selecione **"Open with Live Server"**.

### Opção 2: Node.js (Sem Instalações Adicionais)
Execute no terminal da pasta do projeto:
```bash
npx serve .
# ou
python -m http.server 8000
```
Em seguida, acesse no navegador: `http://localhost:8000` (ou a porta indicada).

---

## 👥 Autores Originais

- Alisson Claro
- Matheus Yuri
- Vinicius
- Rafael Di Pietro
- Pedro Martins

*Projeto Interdisciplinar - Fatec Marília*
