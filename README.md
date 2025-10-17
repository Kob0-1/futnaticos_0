<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>FUTNATICOS</title>

  <!-- Tipografias -->
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@700;800&family=Open+Sans:wght@400;600&display=swap" rel="stylesheet">

  <link rel="stylesheet" href="style.css" />
</head>
<body>
  <!-- Botão do Pânico -->
  <a class="panic-button" href="tel:190" aria-label="Ligar 190">
    <span>190</span>
  </a>

  <!-- Cabeçalho fixo -->
  <header class="header">
    <div class="container header-inner">
      <div class="brand" data-nav="#home">
        <div class="logo-mark" aria-hidden="true">⚽</div>
        <div class="logo-text">FUTNATICOS</div>
      </div>
      <nav class="nav">
        <a class="nav-link active" href="#home">Home</a>
        <a class="nav-link" href="#notificacoes">Notificações</a>
        <a class="nav-link" id="menu-perfil" href="#perfil" style="display:none;">Meu Perfil</a>
        <a class="nav-link" id="menu-login" href="#login">Login/Registrar</a>
        <button class="btn btn-accent btn-small" id="header-criar">
          <span class="icon">＋</span> Criar Partida
        </button>
      </nav>
    </div>
  </header>

  <main>
    <!-- Home -->
    <section id="home" class="screen show">
      <!-- Hero -->
      <section class="hero">
        <div class="hero-overlay"></div>
        <div class="container hero-content">
          <h1 class="hero-title">Encontre ou organize partidas de futebol perto de você</h1>
          <form id="buscaForm" class="search-bar">
            <div class="input">
              <label for="inputLocal">Localização</label>
              <input id="inputLocal" name="local" type="text" placeholder="Use sua localização" />
              <button type="button" class="btn btn-light btn-small" id="btnGeo">Usar minha localização</button>
            </div>
            <div class="input">
              <label for="inputData">Data</label>
              <input id="inputData" name="data" type="date" />
            </div>
            <div class="actions">
              <button class="btn btn-primary" type="submit">Buscar</button>
            </div>
          </form>
        </div>
      </section>

      <!-- Conteúdo Home -->
      <section class="container content-grid">
        <!-- Filtros laterais -->
        <aside class="filters">
          <h3 class="section-title">Filtros</h3>
          <div class="filter-group">
            <label for="filtroBairro"><strong>Bairro:</strong></label>
            <input id="filtroBairro" type="text" placeholder="Ex.: Centro" />
          </div>
          <div class="filter-group">
            <label for="filtroHorario"><strong>Horário:</strong></label>
            <select id="filtroHorario">
              <option value="">Qualquer</option>
              <option value="manha">Manhã</option>
              <option value="tarde">Tarde</option>
              <option value="noite">Noite</option>
            </select>
          </div>
          <div class="filter-group">
            <label for="filtroCampo"><strong>Tipo de campo:</strong></label>
            <select id="filtroCampo">
              <option value="">Todos</option>
              <option value="grama">Grama</option>
              <option value="society">Society</option>
              <option value="futsal">Futsal</option>
            </select>
          </div>
          <div class="filter-group">
            <label for="filtroNivel"><strong>Nível:</strong></label>
            <select id="filtroNivel">
              <option value="">Qualquer</option>
              <option value="iniciante">Iniciante</option>
              <option value="intermediario">Intermediário</option>
              <option value="avancado">Avançado</option>
            </select>
          </div>
          <button id="btnAplicarFiltros" class="btn btn-outline">Aplicar filtros</button>
        </aside>

        <!-- Lista de Partidas -->
        <section class="matches">
          <div class="list-header">
            <h3 class="section-title">Partidas próximas</h3>
            <button class="btn btn-accent" id="home-criar">
              <span class="icon">＋</span> Criar Partida
            </button>
          </div>

          <div id="emptyState" class="empty-state">
            <div class="empty-illustration">🏟️</div>
            <h4>Nenhuma partida registrada ainda</h4>
            <p>Seja o primeiro a organizar um jogo na sua região.</p>
            <button class="btn btn-accent" id="empty-criar">
              <span class="icon">＋</span> Criar Partida
            </button>
          </div>

          <div id="matchesList" class="cards"></div>

          <div id="sugestoes" class="suggestions" style="display:none;">
            <h4>Sugestões para você</h4>
            <div id="sugestoesList" class="cards"></div>
          </div>
        </section>
      </section>
    </section>

    <!-- Criar Partida -->
    <section id="criar" class="screen">
      <div class="container narrow">
        <h2 class="page-title">Criar Partida</h2>
        <form id="criarForm" class="form-card">
          <div class="form-row">
            <div class="field">
              <label for="jogoNome">Nome do jogo</label>
              <input id="jogoNome" type="text" placeholder="Ex.: Pelada de sábado" required />
            </div>
            <div class="field">
              <label for="jogoCampo">Tipo de campo</label>
              <select id="jogoCampo" required>
                <option value="">Selecione</option>
                <option value="grama">Grama</option>
                <option value="society">Society</option>
                <option value="futsal">Futsal</option>
              </select>
            </div>
          </div>

          <div class="form-row">
            <div class="field">
              <label for="jogoData">Data</label>
              <input id="jogoData" type="date" required />
            </div>
            <div class="field">
              <label for="jogoHora">Hora</label>
              <input id="jogoHora" type="time" required />
            </div>
            <div class="field">
              <label for="jogoVagas">Quantidade de jogadores</label>
              <input id="jogoVagas" type="number" min="2" max="30" placeholder="Ex.: 10" required />
            </div>
          </div>

          <div class="form-row">
            <div class="field">
              <label for="jogoValor">Valor de participação (opcional)</label>
              <input id="jogoValor" type="number" min="0" step="1" placeholder="Ex.: 20" />
            </div>
            <div class="field">
              <label for="jogoGenero">Categoria</label>
              <select id="jogoGenero">
                <option value="misto">Misto</option>
                <option value="masculino">Masculino</option>
                <option value="feminino">Feminino</option>
              </select>
            </div>
            <div class="field">
              <label for="jogoNivel">Nível</label>
              <select id="jogoNivel">
                <option value="iniciante">Iniciante</option>
                <option value="intermediario">Intermediário</option>
                <option value="avancado">Avançado</option>
              </select>
            </div>
          </div>

          <div class="field">
            <label for="jogoLocal">Local</label>
            <input id="jogoLocal" type="text" placeholder="Nome do campo, endereço, bairro" required />
          </div>

          <!-- Mapa interativo simples (mock) -->
          <div class="map-wrapper">
            <div class="map" id="mapCriar" aria-label="Mapa interativo">
              <div class="map-help">Clique no mapa para marcar o local (simulado)</div>
              <div class="pin" id="mapCriarPin" style="display:none;"></div>
            </div>
            <div class="map-coords">
              <input id="jogoLat" type="text" placeholder="Lat" readonly />
              <input id="jogoLng" type="text" placeholder="Lng" readonly />
            </div>
          </div>

          <div class="form-row">
            <div class="field checkbox">
              <input id="jogoDividir" type="checkbox" />
              <label for="jogoDividir">Dividir custo do aluguel automaticamente (simulado)</label>
            </div>
            <div class="field">
              <label for="jogoObs">Observações</label>
              <input id="jogoObs" type="text" placeholder="Ex.: Levar colete, 2 tempos de 25min" />
            </div>
          </div>

          <div class="actions">
            <button class="btn btn-accent" type="submit">Publicar Partida</button>
            <button class="btn btn-ghost" type="button" data-nav="#home">Cancelar</button>
          </div>
          <p class="hint">Chat com participantes disponível após publicar a partida.</p>
        </form>
      </div>
    </section>

    <!-- Tela da Partida -->
    <section id="partida" class="screen">
      <div class="container">
        <button class="btn btn-ghost back-btn" data-nav="#home">← Voltar</button>

        <div class="match-header">
          <div class="match-photo" id="partidaFoto" aria-label="Foto do local">🏟️</div>
          <div class="match-info">
            <h2 id="partidaTitulo">Partida</h2>
            <div class="meta">
              <span id="partidaLocal" class="badge"></span>
              <span id="partidaDataHora" class="badge"></span>
              <span id="partidaCampo" class="badge"></span>
              <span id="partidaNivel" class="badge"></span>
              <span id="partidaValor" class="badge"></span>
              <span id="partidaGenero" class="badge"></span>
            </div>
            <div class="actions">
              <button id="btnConfirmar" class="btn btn-primary">Confirmar Presença</button>
              <button id="btnAbrirChat" class="btn btn-outline">Abrir Chat</button>
            </div>
          </div>
        </div>

        <div class="match-body">
          <div class="match-map" id="mapPartida">
            <div class="map" aria-label="Mapa da partida">
              <div class="pin" id="mapPartidaPin" style="display:none;"></div>
            </div>
          </div>

          <div class="match-side">
            <h3 class="section-title">Jogadores confirmados</h3>
            <div id="listaJogadores" class="avatars"></div>

            <h3 class="section-title">Detalhes</h3>
            <ul class="details" id="partidaDetalhes"></ul>
          </div>
        </div>
      </div>

      <!-- Modal de Chat -->
      <div id="chatModal" class="modal">
        <div class="modal-content">
          <div class="modal-header">
            <h3>Chat da Partida</h3>
            <button class="btn btn-ghost modal-close" id="chatClose">✕</button>
          </div>
          <div id="chatMensagens" class="chat"></div>
          <form id="chatForm" class="chat-input">
            <input id="chatTexto" type="text" placeholder="Escreva uma mensagem..." required />
            <button class="btn btn-primary" type="submit">Enviar</button>
          </form>
        </div>
      </div>
    </section>

    <!-- Perfil do Usuário -->
    <section id="perfil" class="screen">
      <div class="container narrow">
        <h2 class="page-title">Meu Perfil</h2>
        <div class="profile-card">
          <div class="profile-left">
            <div id="perfilFoto" class="avatar-xl" aria-label="Foto do perfil">🙂</div>
            <button id="perfilTrocarAvatar" class="btn btn-ghost btn-small">Trocar avatar</button>
          </div>
          <div class="profile-right">
            <div class="field">
              <label for="perfilNome">Nome</label>
              <input id="perfilNome" type="text" placeholder="Seu nome" />
            </div>
            <div class="field">
              <label for="perfilPosicao">Posição favorita</label>
              <select id="perfilPosicao">
                <option value="">Selecione</option>
                <option value="goleiro">Goleiro</option>
                <option value="zagueiro">Zagueiro</option>
                <option value="lateral">Lateral</option>
                <option value="meia">Meia</option>
                <option value="atacante">Atacante</option>
              </select>
            </div>
            <div class="field">
              <label for="perfilNivel">Nível</label>
              <select id="perfilNivel">
                <option value="iniciante">Iniciante</option>
                <option value="intermediario">Intermediário</option>
                <option value="avancado">Avançado</option>
              </select>
            </div>
            <div class="stats">
              <div class="stat">
                <div class="stat-value" id="statPartidas">0</div>
                <div class="stat-label">Partidas jogadas</div>
              </div>
              <div class="stat">
                <div class="stat-value" id="statGols">0</div>
                <div class="stat-label">Gols marcados</div>
              </div>
              <div class="stat">
                <div class="stat-value" id="statRanking">0</div>
                <div class="stat-label">Ranking de presença</div>
              </div>
            </div>
            <div class="field">
              <label for="perfilAvaliacoes">Avaliações recebidas</label>
              <input id="perfilAvaliacoes" type="text" placeholder="Ex.: Pontual, Bom jogador" />
            </div>
            <div class="actions">
              <button id="perfilSalvar" class="btn btn-primary">Salvar</button>
              <button id="perfilSair" class="btn btn-outline">Sair</button>
            </div>
          </div>
        </div>

        <h3 class="section-title">Histórico de partidas</h3>
        <div id="perfilHistorico" class="cards"></div>
      </div>
    </section>

    <!-- Notificações -->
    <section id="notificacoes" class="screen">
      <div class="container narrow">
        <h2 class="page-title">Notificações</h2>
        <div id="notificacoesLista" class="notifications"></div>
      </div>
    </section>

    <!-- Login / Registrar -->
    <section id="login" class="screen">
      <div class="container narrow">
        <h2 class="page-title">Entrar</h2>
        <div class="login-card">
          <form id="loginForm" class="form">
            <div class="field">
              <label for="loginNome">Seu nome</label>
              <input id="loginNome" type="text" placeholder="Como quer aparecer" required />
            </div>
            <div class="field">
              <label for="loginEmail">Email</label>
              <input id="loginEmail" type="email" placeholder="voce@email.com" required />
            </div>
            <div class="actions">
              <button class="btn btn-primary" type="submit">Entrar</button>
            </div>
          </form>

          <div class="login-divider">ou</div>

          <div class="login-social">
            <button id="loginGoogle" class="btn btn-ghost">Entrar com Google (simulado)</button>
            <button id="loginFacebook" class="btn btn-ghost">Entrar com Facebook (simulado)</button>
          </div>
        </div>
      </div>
    </section>
  </main>

  <!-- Rodapé -->
  <footer class="footer">
    <div class="container footer-inner">
      <div class="footer-brand">
        <div class="logo-mark">⚽</div>
        <div class="logo-text small">FUTNATICOS</div>
      </div>
      <div class="footer-links">
        <a href="#" class="footer-link">Sobre</a>
        <a href="#" class="footer-link">Contato</a>
        <a href="#" class="footer-link">Política de Privacidade</a>
      </div>
      <div class="footer-social">
        <a class="social" href="#" aria-label="Instagram">📸</a>
        <a class="social" href="#" aria-label="X/Twitter">𝕏</a>
        <a class="social" href="#" aria-label="YouTube">▶️</a>
      </div>
    </div>
  </footer>

  <script src="script.js"></script>
</body>
</html>


:root{
  --green:#2E7D32;
  --black:#000000;
  --white:#FFFFFF;
  --yellow:#FFD600;
  --light:#F5F5F5;
  --text:#1b1b1b;
  --muted:#6b6b6b;
  --card: #ffffff;
  --shadow: 0 8px 24px rgba(0,0,0,0.08);
  --radius: 14px;
}

*{box-sizing:border-box}
html,body{height:100%}
body{
  margin:0;
  color:var(--text);
  background:var(--white);
  font-family: "Open Sans", system-ui, -apple-system, Segoe UI, Roboto, Arial, sans-serif;
}

/* Cabeçalho */
.header{
  position:sticky; top:0; z-index:50;
  background:var(--white);
  border-bottom:1px solid #eaeaea;
}
.container{width:min(1120px, 92%); margin:0 auto}
.header-inner{
  display:flex; align-items:center; justify-content:space-between;
  padding:12px 0;
}
.brand{display:flex; align-items:center; gap:10px; cursor:pointer}
.logo-mark{
  width:36px; height:36px; display:grid; place-items:center;
  background:var(--green); color:#fff; border-radius:10px; font-size:18px;
}
.logo-text{
  font-family:"Montserrat", sans-serif; font-weight:800; letter-spacing:0.5px;
}
.logo-text.small{font-weight:700; font-size:14px}
.nav{display:flex; align-items:center; gap:16px}
.nav-link{
  text-decoration:none; color:var(--text); padding:8px 10px; border-radius:8px;
}
.nav-link.active{background:var(--light)}
.btn{
  display:inline-flex; align-items:center; justify-content:center; gap:8px;
  border:none; border-radius:12px; padding:12px 18px; cursor:pointer;
  font-weight:600; box-shadow:var(--shadow); transition:transform .02s ease-in;
}
.btn:active{transform:translateY(1px)}
.btn-small{padding:8px 12px; border-radius:10px; font-size:14px; box-shadow:none}
.btn-primary{background:var(--green); color:#fff}
.btn-accent{background:var(--yellow); color:#1b1b1b}
.btn-outline{background:#fff; color:var(--text); border:1px solid #ddd; box-shadow:none}
.btn-light{background:#fff; color:var(--text); border:1px solid #ddd}
.btn-ghost{background:transparent; color:var(--text); box-shadow:none}

.icon{font-size:18px; line-height:1}

/* Panic button */
.panic-button{
  position:fixed; right:16px; bottom:16px; z-index:60;
  width:64px; height:64px; border-radius:50%;
  background:#ff3b30; color:#fff; display:grid; place-items:center;
  text-decoration:none; font-weight:800; box-shadow:0 10px 24px rgba(255,59,48,.3);
}

/* Screens */
.screen{display:none; padding-top:16px}
.screen.show{display:block}

/* Hero com textura de “grama” */
.hero{
  position:relative;
  min-height:44vh;
  display:flex; align-items:center;
  background:
    repeating-linear-gradient(90deg, rgba(255,255,255,0.02) 0, rgba(255,255,255,0.02) 6px, transparent 6px, transparent 12px),
    linear-gradient(180deg, rgba(0,0,0,0.1), rgba(0,0,0,0.15)),
    radial-gradient(ellipse at center, #2e7d32 0%, #245e27 100%);
  color:#fff;
}
.hero-overlay{position:absolute; inset:0; background:rgba(0,0,0,0.25)}
.hero-content{position:relative; z-index:1; padding:36px 0}
.hero-title{
  font-family:"Montserrat", sans-serif; font-weight:800; margin:0 0 18px 0; max-width:820px;
}
.search-bar{
  display:grid; grid-template-columns: 1.2fr 0.8fr auto; gap:12px;
  background:rgba(255,255,255,0.9); padding:12px; border-radius:14px; color:var(--text);
  box-shadow: var(--shadow);
}
.search-bar .input{display:flex; flex-direction:column; gap:6px}
.search-bar label{font-size:12px; color:var(--muted)}
.search-bar input{padding:12px; border:1px solid #ddd; border-radius:10px}
.search-bar .actions{display:flex; align-items:flex-end}
.search-bar .btn-primary{min-width:140px}

/* Grid Home */
.content-grid{
  display:grid; grid-template-columns: 280px 1fr; gap:24px; margin:28px auto 40px auto;
}
.filters{
  position:sticky; top:76px; align-self:start;
  background:var(--card); border-radius:var(--radius); padding:16px; box-shadow:var(--shadow);
}
.filter-group{display:flex; flex-direction:column; gap:8px; margin-bottom:12px}
.filter-group input, .filter-group select{
  padding:10px; border:1px solid #e3e3e3; border-radius:10px; background:#fff;
}
.matches .list-header{
  display:flex; align-items:center; justify-content:space-between; margin-bottom:12px;
}
.section-title{
  font-family:"Montserrat", sans-serif; font-weight:800; margin:0 0 8px 0;
}

/* Cards */
.cards{
  display:grid; grid-template-columns: repeat( auto-fill, minmax(280px, 1fr)); gap:16px;
}
.card{
  background:var(--card); border-radius:var(--radius); box-shadow:var(--shadow);
  padding:14px; display:flex; flex-direction:column; gap:10px;
}
.card .title{font-weight:700}
.badge{
  display:inline-flex; align-items:center; gap:6px;
  background:var(--light); border-radius:999px; padding:6px 10px; font-size:12px; color:#333;
}
.card .meta{display:flex; flex-wrap:wrap; gap:8px}
.card .mini-map{
  background:linear-gradient(135deg, #ececec, #fafafa);
  border-radius:12px; height:120px; position:relative;
}
.card .mini-pin{
  position:absolute; width:12px; height:12px; border-radius:50%; background:var(--green); border:2px solid #fff;
  transform:translate(-50%,-50%);
}
.card .footer{display:flex; align-items:center; justify-content:space-between; margin-top:8px}

/* Empty state */
.empty-state{
  background:var(--card); border-radius:var(--radius); box-shadow:var(--shadow);
  padding:24px; text-align:center; margin:12px 0;
}
.empty-illustration{font-size:36px; margin-bottom:6px}

/* Criar Partida */
.page-title{
  font-family:"Montserrat", sans-serif; font-weight:800; margin:8px 0 16px 0;
}
.narrow{max-width:860px}
.form-card{
  background:var(--card); border-radius:var(--radius); box-shadow:var(--shadow);
  padding:18px; display:flex; flex-direction:column; gap:14px;
}
.form-row{display:grid; grid-template-columns: repeat(3, 1fr); gap:12px}
.field{display:flex; flex-direction:column; gap:6px}
.field.checkbox{flex-direction:row; align-items:center; gap:8px}
.field input, .field select{
  padding:12px; border:1px solid #e3e3e3; border-radius:10px; background:#fff;
}
.hint{color:var(--muted); font-size:13px}
.actions{display:flex; gap:10px; align-items:center}

.map-wrapper{display:grid; grid-template-columns: 1fr 220px; gap:12px; align-items:start}
.map{
  background:linear-gradient(90deg, #eaeaea 10px, transparent 1px) center/22px 22px,
             linear-gradient(#eaeaea 10px, transparent 1px) center/22px 22px,
             #f7f7f7;
  height:220px; border-radius:12px; position:relative; border:1px solid #e5e5e5;
}
.map-help{
  position:absolute; bottom:10px; left:10px; font-size:12px; color:#666; background:#fff;
  padding:4px 8px; border-radius:8px; border:1px solid #eee;
}
.map-coords input{width:100%; margin-bottom:8px}
.pin{
  position:absolute; width:16px; height:16px; border-radius:50%; background:var(--green);
  border:3px solid #fff; box-shadow:0 4px 12px rgba(0,0,0,0.25);
  transform:translate(-50%,-50%);
}

/* Partida */
.back-btn{margin:8px 0}
.match-header{
  display:grid; grid-template-columns: 160px 1fr; gap:16px; margin-bottom:16px;
}
.match-photo{
  width:100%; height:160px; border-radius:16px; background:linear-gradient(135deg, #d9f0dc, #a6d6ad);
  display:grid; place-items:center; font-size:42px;
}
.match-info .meta{display:flex; flex-wrap:wrap; gap:8px; margin:8px 0}
.match-body{
  display:grid; grid-template-columns: 1.2fr 0.8fr; gap:16px; align-items:start;
}
.match-map .map{height:320px}
.avatars{display:flex; flex-wrap:wrap; gap:10px}
.avatar{
  width:44px; height:44px; border-radius:50%; background:#eaeaea; display:grid; place-items:center; font-weight:700;
}
.avatar-xl{width:80px; height:80px; border-radius:50%; background:#eaeaea; display:grid; place-items:center; font-size:34px}
.details{list-style:none; padding:0; margin:0}
.details li{padding:8px 10px; background:#fff; border:1px solid #eee; border-radius:10px; margin-bottom:8px}

/* Modal */
.modal{position:fixed; inset:0; display:none; place-items:center; background:rgba(0,0,0,0.45); z-index:70}
.modal.show{display:grid}
.modal-content{
  width:min(720px, 92%); background:#fff; border-radius:16px; box-shadow:var(--shadow); overflow:hidden;
  display:grid; grid-template-rows: auto 1fr auto;
}
.modal-header{display:flex; align-items:center; justify-content:space-between; padding:12px 14px; border-bottom:1px solid #eee}
.chat{padding:14px; display:flex; flex-direction:column; gap:10px; max-height:50vh; overflow:auto; background:#fafafa}
.chat .msg{
  background:#fff; border:1px solid #eee; border-radius:10px; padding:10px 12px; max-width:80%;
}
.chat .me{align-self:flex-end; background:#e7f7ea; border-color:#d7eedc}
.chat-input{display:flex; gap:10px; padding:10px; border-top:1px solid #eee}
.chat-input input{flex:1; padding:12px; border:1px solid #e3e3e3; border-radius:10px}

/* Perfil */
.profile-card{
  display:grid; grid-template-columns: 140px 1fr; gap:16px;
  background:#fff; border-radius:16px; box-shadow:var(--shadow); padding:16px;
}
.profile-left{display:flex; flex-direction:column; align-items:center; gap:10px}
.stats{display:grid; grid-template-columns: repeat(3, 1fr); gap:12px; margin:10px 0}
.stat{background:#fff; border:1px solid #eee; border-radius:12px; padding:10px; text-align:center}
.stat-value{font-family:"Montserrat"; font-weight:800; font-size:20px}

/* Notificações */
.notifications{display:flex; flex-direction:column; gap:10px}
.notification{
  background:#fff; border:1px solid #eee; border-radius:12px; padding:12px; display:flex; justify-content:space-between; align-items:center;
}

/* Rodapé */
.footer{border-top:1px solid #eee; background:#fff; margin-top:40px}
.footer-inner{display:flex; align-items:center; justify-content:space-between; padding:16px 0}
.footer-links, .footer-social{display:flex; gap:14px}
.footer-link, .social{color:var(--muted); text-decoration:none}

/* Responsivo */
@media (max-width: 980px){
  .content-grid{grid-template-columns: 1fr}
  .filters{position:relative; top:auto}
  .form-row{grid-template-columns: 1fr}
  .map-wrapper{grid-template-columns: 1fr}
  .match-header{grid-template-columns: 1fr}
  .match-body{grid-template-columns: 1fr}
}

// Estado simples em localStorage
const STORE_KEY = 'futnaticos_store_v1';
const initialStore = {
  user: null,
  matches: [],           // começa vazio: "Nenhuma partida registrada"
  notifications: []
};

let store = loadStore();

// Utilitários de Store
function loadStore(){
  try{
    const raw = localStorage.getItem(STORE_KEY);
    return raw ? JSON.parse(raw) : structuredClone(initialStore);
  }catch(e){
    return structuredClone(initialStore);
  }
}
function saveStore(){
  localStorage.setItem(STORE_KEY, JSON.stringify(store));
}

// Navegação SPA
const screens = Array.from(document.querySelectorAll('.screen'));
function showScreen(hash){
  const target = hash || '#home';
  screens.forEach(s => s.classList.toggle('show', '#'+s.id === target));
  // menu ativo
  document.querySelectorAll('.nav-link').forEach(a => {
    a.classList.toggle('active', a.getAttribute('href') === target);
  });
}
window.addEventListener('hashchange', () => showScreen(location.hash));
document.querySelectorAll('[data-nav]').forEach(el=>{
  el.addEventListener('click', (e)=>{
    const to = el.getAttribute('data-nav');
    if(to){ location.hash = to; }
  });
});

// Header ações
document.getElementById('header-criar').addEventListener('click', ()=> location.hash = '#criar');

// Home botões "Criar Partida"
['home-criar','empty-criar'].forEach(id=>{
  const el = document.getElementById(id);
  if(el) el.addEventListener('click', ()=> location.hash = '#criar');
});

// Geolocalização simples
document.getElementById('btnGeo').addEventListener('click', ()=>{
  if(!navigator.geolocation){
    alert('Geolocalização indisponível no seu navegador.');
    return;
  }
  navigator.geolocation.getCurrentPosition((pos)=>{
    const {latitude, longitude} = pos.coords;
    document.getElementById('inputLocal').value = `Minha localização (${latitude.toFixed(4)}, ${longitude.toFixed(4)})`;
  }, ()=>{
    alert('Não foi possível obter sua localização.');
  });
});

// Busca
document.getElementById('buscaForm').addEventListener('submit', (e)=>{
  e.preventDefault();
  renderMatches(); // com filtros já aplicados
});

// Filtros
document.getElementById('btnAplicarFiltros').addEventListener('click', renderMatches);

// Render inicial
renderHeaderByAuth();
renderMatches();
renderNotificacoes();

// Mostrar tela inicial
showScreen(location.hash || '#home');

/* ------------------ MATCHES LIST ------------------ */
function renderMatches(){
  const list = document.getElementById('matchesList');
  const empty = document.getElementById('emptyState');

  const filtroBairro = document.getElementById('filtroBairro').value.trim().toLowerCase();
  const filtroHorario = document.getElementById('filtroHorario').value;
  const filtroCampo = document.getElementById('filtroCampo').value;
  const filtroNivel = document.getElementById('filtroNivel').value;

  let items = [...store.matches];

  // Aplicar filtros
  items = items.filter(m=>{
    let ok = true;
    if(filtroBairro && !(m.local||'').toLowerCase().includes(filtroBairro)) ok=false;
    if(filtroCampo && m.campo !== filtroCampo) ok=false;
    if(filtroNivel && m.nivel !== filtroNivel) ok=false;
    if(filtroHorario){
      const hora = m.hora || '00:00';
      const h = parseInt(hora.split(':')[0],10);
      if(filtroHorario==='manha' && !(h>=6 && h<12)) ok=false;
      if(filtroHorario==='tarde' && !(h>=12 && h<18)) ok=false;
      if(filtroHorario==='noite' && !(h>=18 || h<6)) ok=false;
    }
    return ok;
  });

  list.innerHTML = '';
  if(items.length===0){
    empty.style.display = 'block';
  }else{
    empty.style.display = 'none';
    items.forEach(m=>{
      const card = document.createElement('div');
      card.className = 'card';

      const title = document.createElement('div');
      title.className = 'title';
      title.textContent = m.nome;

      const meta = document.createElement('div');
      meta.className = 'meta';
      meta.innerHTML = `
        <span class="badge">📍 ${m.local || 'A definir'}</span>
        <span class="badge">🗓️ ${formatDate(m.data)} ${m.hora ? 'às '+m.hora : ''}</span>
        <span class="badge">👥 ${Math.max(0, m.vagas - (m.jogadores?.length||0))} vagas</span>
        <span class="badge">🏟️ ${labelCampo(m.campo)}</span>
        ${m.nivel ? `<span class="badge">🎯 ${labelNivel(m.nivel)}</span>`:''}
        ${m.valor ? `<span class="badge">💵 R$ ${Number(m.valor).toFixed(2)}</span>`:''}
        <span class="badge">⚧ ${m.genero || 'Misto'}</span>
      `;

      const miniMap = document.createElement('div');
      miniMap.className = 'mini-map';
      if(m.lat && m.lng){
        const pin = document.createElement('div');
        pin.className = 'mini-pin';
        pin.style.left = (50 + (m.lng % 1)*30)+'%';
        pin.style.top = (50 + (m.lat % 1)*20)+'%';
        miniMap.appendChild(pin);
      }

      const footer = document.createElement('div');
      footer.className = 'footer';
      const btnJoin = document.createElement('button');
      btnJoin.className = 'btn btn-primary btn-small';
      btnJoin.textContent = 'Participar';
      btnJoin.addEventListener('click', ()=>{
        openPartida(m.id);
      });

      const btnVer = document.createElement('button');
      btnVer.className = 'btn btn-outline btn-small';
      btnVer.textContent = 'Ver detalhes';
      btnVer.addEventListener('click', ()=> openPartida(m.id));

      footer.appendChild(btnJoin);
      footer.appendChild(btnVer);

      card.appendChild(title);
      card.appendChild(meta);
      card.appendChild(miniMap);
      card.appendChild(footer);
      list.appendChild(card);
    });
  }

  // Sugestões automáticas baseadas no perfil (simples)
  const sugWrap = document.getElementById('sugestoes');
  const sugList = document.getElementById('sugestoesList');
  if(store.user && store.matches.length>0){
    const nivel = store.user.nivel || '';
    const bairro = ''; // poderia inferir do nome do local
    const sugestoes = store.matches.filter(m=>{
      let ok = true;
      if(nivel && m.nivel && m.nivel!==nivel) ok=false;
      return ok;
    }).slice(0,3);
    if(sugestoes.length){
      sugWrap.style.display = 'block';
      sugList.innerHTML = '';
      sugestoes.forEach(m=>{
        const c = document.createElement('div');
        c.className='card';
        c.innerHTML = `
          <div class="title">${m.nome}</div>
          <div class="meta">
            <span class="badge">📍 ${m.local||'A definir'}</span>
            <span class="badge">🗓️ ${formatDate(m.data)} ${m.hora?'às '+m.hora:''}</span>
          </div>
          <div class="footer">
            <button class="btn btn-primary btn-small" data-id="${m.id}">Participar</button>
          </div>
        `;
        c.querySelector('button').addEventListener('click', ()=> openPartida(m.id));
        sugList.appendChild(c);
      });
    }else{
      sugWrap.style.display = 'none';
    }
  }else{
    sugWrap.style.display = 'none';
  }
}

/* ------------------ CRIAR PARTIDA ------------------ */
document.getElementById('criarForm').addEventListener('submit', (e)=>{
  e.preventDefault();
  const nome = document.getElementById('jogoNome').value.trim();
  const campo = document.getElementById('jogoCampo').value;
  const data = document.getElementById('jogoData').value;
  const hora = document.getElementById('jogoHora').value;
  const vagas = parseInt(document.getElementById('jogoVagas').value,10)||0;
  const valor = document.getElementById('jogoValor').value;
  const genero = document.getElementById('jogoGenero').value;
  const nivel = document.getElementById('jogoNivel').value;
  const local = document.getElementById('jogoLocal').value.trim();
  const lat = parseFloat(document.getElementById('jogoLat').value) || null;
  const lng = parseFloat(document.getElementById('jogoLng').value) || null;
  const obs = document.getElementById('jogoObs').value.trim();
  const dividir = document.getElementById('jogoDividir').checked;

  const id = 'm_'+Date.now();
  const owner = store.user ? store.user.id : null;

  const match = {
    id, nome, campo, data, hora, vagas, valor, genero, nivel, local, lat, lng, obs, dividir,
    owner,
    jogadores: [],
    chat: []
  };
  store.matches.unshift(match);
  saveStore();

  // Notificação
  pushNotif('Partida publicada', `“${nome}” foi publicada para ${formatDate(data)} ${hora? 'às '+hora:''}.`);

  // Vai para a tela da partida
  openPartida(id);
});

// Mapa (mock): clique para posicionar
const mapCriar = document.getElementById('mapCriar');
const mapCriarPin = document.getElementById('mapCriarPin');
mapCriar.addEventListener('click', (e)=>{
  const rect = mapCriar.getBoundingClientRect();
  const x = e.clientX - rect.left;
  const y = e.clientY - rect.top;
  const pctX = x / rect.width;
  const pctY = y / rect.height;

  // Converter posição clicada em coordenadas simuladas
  const lat = (-23.43 + (pctY-0.5)*0.2).toFixed(6);
  const lng = (-48.17 + (pctX-0.5)*0.2).toFixed(6);

  mapCriarPin.style.left = (pctX*100)+'%';
  mapCriarPin.style.top = (pctY*100)+'%';
  mapCriarPin.style.display = 'block';

  document.getElementById('jogoLat').value = lat;
  document.getElementById('jogoLng').value = lng;
});

/* ------------------ PARTIDA ------------------ */
function openPartida(id){
  const m = store.matches.find(x=>x.id===id);
  if(!m){ alert('Partida não encontrada.'); return; }

  // Popular campos
  document.getElementById('partidaTitulo').textContent = m.nome;
  document.getElementById('partidaLocal').textContent = m.local || 'Local a definir';
  document.getElementById('partidaDataHora').textContent = `${formatDate(m.data)} ${m.hora? 'às '+m.hora:''}`;
  document.getElementById('partidaCampo').textContent = labelCampo(m.campo);
  document.getElementById('partidaNivel').textContent = labelNivel(m.nivel);
  document.getElementById('partidaValor').textContent = m.valor ? `R$ ${Number(m.valor).toFixed(2)}` : 'Gratuito';
  document.getElementById('partidaGenero').textContent = (m.genero||'Misto');

  // Detalhes
  const detalhes = document.getElementById('partidaDetalhes');
  detalhes.innerHTML = '';
  addDetail(detalhes, 'Vagas', `${Math.max(0, m.vagas - (m.jogadores?.length||0))} de ${m.vagas}`);
  if(m.obs) addDetail(detalhes, 'Observações', m.obs);
  addDetail(detalhes, 'Dividir custo', m.dividir ? 'Ativado (simulado)' : 'Não');
  if(m.owner && store.user && m.owner===store.user.id) addDetail(detalhes, 'Você é o organizador', 'Sim');

  // Jogadores
  const lista = document.getElementById('listaJogadores');
  lista.innerHTML = '';
  (m.jogadores||[]).forEach(u=>{
    lista.appendChild(avatarEl(u));
  });

  // Mapa da partida (mock)
  const pin = document.getElementById('mapPartidaPin');
  if(m.lat && m.lng){
    pin.style.left = (50 + (m.lng % 1)*30)+'%';
    pin.style.top = (50 + (m.lat % 1)*20)+'%';
    pin.style.display = 'block';
  }else{
    pin.style.display = 'none';
  }

  // Botões
  const btnConfirmar = document.getElementById('btnConfirmar');
  btnConfirmar.onclick = ()=>{
    if(!store.user){ return goLogin('Entre para confirmar presença.'); }
    const ja = (m.jogadores||[]).some(j=> j.id === store.user.id);
    if(ja){
      alert('Você já está confirmado nesta partida.');
      return;
    }
    if((m.jogadores?.length||0) >= m.vagas){
      alert('Não há vagas disponíveis.');
      return;
    }
    m.jogadores.push(minUser(store.user));
    saveStore();
    pushNotif('Confirmação de presença', `Você confirmou presença em “${m.nome}”.`);
    // ranking de presença
    store.user.ranking = (store.user.ranking||0) + 1;
    saveStore();
    // atualizar UI
    openPartida(m.id);
  };

  document.getElementById('btnAbrirChat').onclick = ()=>{
    if(!store.user){ return goLogin('Entre para participar do chat.'); }
    openChat(m.id);
  };

  // Navega
  location.hash = '#partida';
}

function addDetail(list, label, value){
  const li = document.createElement('li');
  li.innerHTML = `<strong>${label}:</strong> ${value}`;
  list.appendChild(li);
}

function labelCampo(c){
  if(c==='grama') return 'Grama';
  if(c==='society') return 'Society';
  if(c==='futsal') return 'Futsal';
  return 'Campo';
}
function labelNivel(n){
  if(n==='iniciante') return 'Iniciante';
  if(n==='intermediario') return 'Intermediário';
  if(n==='avancado') return 'Avançado';
  return 'Nível';
}
function formatDate(iso){
  if(!iso) return 'Data a definir';
  const [y,m,d] = iso.split('-').map(Number);
  if(!y||!m||!d) return iso;
  return `${d.toString().padStart(2,'0')}/${m.toString().padStart(2,'0')}/${y}`;
}

/* ------------------ CHAT ------------------ */
const chatModal = document.getElementById('chatModal');
document.getElementById('chatClose').addEventListener('click', ()=> chatModal.classList.remove('show'));

function openChat(matchId){
  chatModal.dataset.matchId = matchId;
  renderChat();
  chatModal.classList.add('show');
}

function renderChat(){
  const matchId = chatModal.dataset.matchId;
  const m = store.matches.find(x=>x.id===matchId);
  const box = document.getElementById('chatMensagens');
  box.innerHTML = '';
  (m.chat||[]).forEach(msg=>{
    const div = document.createElement('div');
    div.className = 'msg' + (store.user && msg.userId===store.user.id ? ' me' : '');
    div.innerHTML = `<strong>${msg.userName}:</strong> ${escapeHTML(msg.text)} <div style="font-size:11px;color:#888;">${new Date(msg.ts).toLocaleString()}</div>`;
    box.appendChild(div);
  });
  box.scrollTop = box.scrollHeight;
}

document.getElementById('chatForm').addEventListener('submit', (e)=>{
  e.preventDefault();
  const matchId = chatModal.dataset.matchId;
  const m = store.matches.find(x=>x.id===matchId);
  if(!m){ return; }
  const text = document.getElementById('chatTexto').value.trim();
  if(!text) return;
  if(!store.user){ return goLogin('Entre para enviar mensagens.'); }

  m.chat = m.chat || [];
  m.chat.push({
    userId: store.user.id,
    userName: store.user.nome || 'Você',
    text,
    ts: Date.now()
  });
  saveStore();
  document.getElementById('chatTexto').value = '';
  renderChat();
});

/* ------------------ PERFIL ------------------ */
function avatarEl(user){
  const d = document.createElement('div');
  d.className = 'avatar';
  d.title = user.nome || 'Jogador';
  d.textContent = initials(user.nome || '?');
  return d;
}
function initials(name){
  return name.split(' ').slice(0,2).map(p=>p[0]||'').join('').toUpperCase();
}
function minUser(u){ return { id:u.id, nome:u.nome, posicao:u.posicao || '', nivel:u.nivel || '' }; }

function renderPerfil(){
  if(!store.user) return;
  document.getElementById('perfilNome').value = store.user.nome || '';
  document.getElementById('perfilPosicao').value = store.user.posicao || '';
  document.getElementById('perfilNivel').value = store.user.nivel || 'iniciante';
  document.getElementById('perfilAvaliacoes').value = store.user.avaliacoes || '';
  document.getElementById('statPartidas').textContent = store.user.partidas || 0;
  document.getElementById('statGols').textContent = store.user.gols || 0;
  document.getElementById('statRanking').textContent = store.user.ranking || 0;

  const hist = document.getElementById('perfilHistorico');
  hist.innerHTML = '';
  const played = store.matches.filter(m => (m.jogadores||[]).some(j=>j.id===store.user.id));
  played.forEach(m=>{
    const c = document.createElement('div');
    c.className='card';
    c.innerHTML = `
      <div class="title">${m.nome}</div>
      <div class="meta">
        <span class="badge">📍 ${m.local||'A definir'}</span>
        <span class="badge">🗓️ ${formatDate(m.data)} ${m.hora? 'às '+m.hora:''}</span>
      </div>
    `;
    hist.appendChild(c);
  });
}

document.getElementById('perfilSalvar').addEventListener('click', ()=>{
  if(!store.user) return;
  store.user.nome = document.getElementById('perfilNome').value.trim() || store.user.nome;
  store.user.posicao = document.getElementById('perfilPosicao').value;
  store.user.nivel = document.getElementById('perfilNivel').value;
  store.user.avaliacoes = document.getElementById('perfilAvaliacoes').value.trim();
  saveStore();
  renderHeaderByAuth();
  alert('Perfil salvo!');
});

document.getElementById('perfilSair').addEventListener('click', ()=>{
  store.user = null;
  saveStore();
  renderHeaderByAuth();
  location.hash = '#home';
});

document.getElementById('perfilTrocarAvatar').addEventListener('click', ()=>{
  alert('Use sua criatividade: este demo usa iniciais como avatar 😉');
});

/* ------------------ NOTIFICAÇÕES ------------------ */
function pushNotif(title, text){
  store.notifications.unshift({ id:'n_'+Date.now(), title, text, ts: Date.now(), read:false });
  saveStore();
  renderNotificacoes();
}
function renderNotificacoes(){
  const wrap = document.getElementById('notificacoesLista');
  if(!wrap) return;
  wrap.innerHTML = '';
  if((store.notifications||[]).length===0){
    const empty = document.createElement('div');
    empty.className = 'empty-state';
    empty.innerHTML = '<h4>Sem notificações</h4><p>Você verá lembretes, convites e alterações aqui.</p>';
    wrap.appendChild(empty);
    return;
  }
  store.notifications.forEach(n=>{
    const row = document.createElement('div');
    row.className = 'notification';
    row.innerHTML = `
      <div>
        <div><strong>${n.title}</strong></div>
        <div style="color:#666; font-size:13px;">${n.text}</div>
      </div>
      <div style="font-size:12px; color:#888;">${new Date(n.ts).toLocaleString()}</div>
    `;
    wrap.appendChild(row);
  });
}

/* ------------------ LOGIN ------------------ */
function renderHeaderByAuth(){
  const perfil = document.getElementById('menu-perfil');
  const login = document.getElementById('menu-login');
  if(store.user){
    perfil.style.display = '';
    login.textContent = 'Sair';
    login.href = '#home';
    login.onclick = (e)=>{
      e.preventDefault();
      store.user = null;
      saveStore();
      renderHeaderByAuth();
      location.hash = '#home';
    };
  }else{
    perfil.style.display = 'none';
    login.textContent = 'Login/Registrar';
    login.href = '#login';
    login.onclick = null;
  }
}
function goLogin(msg){
  if(msg) alert(msg);
  location.hash = '#login';
}

// Login formulário
document.getElementById('loginForm').addEventListener('submit', (e)=>{
  e.preventDefault();
  const nome = document.getElementById('loginNome').value.trim();
  const email = document.getElementById('loginEmail').value.trim();
  if(!nome || !email) return;
  store.user = { id: 'u_'+Date.now(), nome, email, nivel:'intermediario', partidas:0, gols:0, ranking:0 };
  saveStore();
  renderHeaderByAuth();
  renderPerfil();
  pushNotif('Bem-vindo!', `Olá, ${nome}! Explore partidas ou crie a sua.`);
  location.hash = '#home';
});

// Login social (simulado)
document.getElementById('loginGoogle').addEventListener('click', ()=>{
  store.user = { id: 'u_'+Date.now(), nome:'Jogador Google', email:'google@exemplo.com', nivel:'iniciante', partidas:0, gols:0, ranking:0 };
  saveStore(); renderHeaderByAuth(); renderPerfil(); pushNotif('Login', 'Você entrou com Google (simulado).'); location.hash = '#home';
});
document.getElementById('loginFacebook').addEventListener('click', ()=>{
  store.user = { id: 'u_'+Date.now(), nome:'Jogador Facebook', email:'facebook@exemplo.com', nivel:'intermediario', partidas:0, gols:0, ranking:0 };
  saveStore(); renderHeaderByAuth(); renderPerfil(); pushNotif('Login', 'Você entrou com Facebook (simulado).'); location.hash = '#home';
});

/* ------------------ EVENTOS DIVERSOS ------------------ */
document.querySelectorAll('a.nav-link[href="#perfil"]').forEach(a => {
  a.addEventListener('click', ()=>{
    if(!store.user){ goLogin('Entre para acessar o seu perfil.'); }
    else renderPerfil();
  });
});

document.querySelectorAll('a.nav-link[href="#home"]').forEach(a=>{
  a.addEventListener('click', ()=> renderMatches());
});

document.querySelector('.brand').addEventListener('click', ()=> location.hash = '#home');

/* ------------------ HELPERS ------------------ */
function escapeHTML(str){
  return str.replace(/[&<>"']/g, m => ({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;',"'":'&#039;'}[m]));
}
```

