<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <title>Chamada de Senhas</title>
  <style>
    
	body {
      font-family: Arial, sans-serif;
      background-color: #f1f3f5;
      margin: 0;
      padding-left: 0;
      display: flex;
      flex-direction: column;
      height: 100vh; /* Garante que o body ocupe toda a altura da tela */
      overflow: hidden;
    }

    h2 {
      text-align: center;
	  font-size: 30px;
      position: sticky;
      top: 40px;
      background-color: #f1f3f5;
      padding: 10px 0;
      margin: 0;
      z-index: 1000;
    }

    .chamada-nome {
      display: flex;
      flex-direction: column;
      align-items: center;
      position: sticky;
      top: 80px;
      background-color: #f1f3f5;
      z-index: 900;
	    padding: 50px;

      
    }

    .chamada-nome input {
      width: 100%;
      max-width: 600px;
      padding: 10px;
      font-size: 18px;
      margin-bottom: 0; /* Sem espaço abaixo */
	  
    }

    .chamada-nome .botoes {
      display: flex;
      gap: 10px;
      flex-wrap: wrap;
      justify-content: center;
	  padding: 10px 0;
	  z-index: 9999;
    }

    .chamada-nome button {
      padding: 10px 20px;
      font-size: 16px;
      cursor: pointer;
	
    }

    .botoes-chamada button {
      padding: 10px 20px;
      font-size: 16px;
      cursor: pointer;
      min-width: 200px;
      z-index: 9999;
      
    }

    /* Grid único com 6 colunas */
    .grid-container {
      display: grid;
      grid-template-columns: repeat(6, 1fr); /* 6 colunas */
      gap: 10px;
      flex-grow: 1; /* Faz com que o grid ocupe todo o espaço restante */
      overflow-y: auto; /* Rolagem habilitada para o grid inteiro */
      max-height: auto;
      margin: 2px;
      margin-top: 0px;
	  margin-bottom: 30px;
      overflow-x: hidden; /* Evita rolagem horizontal */
    }

    .coluna {
      display: flex;
      flex-direction: column;
      height: 100%;
    }

    /* Títulos fixos no topo das colunas */
    .titulo-coluna {
      font-weight: bold;
	  font-size: 20px;
      text-align: center;
      margin-bottom: 10px;
      padding: 5px;
      background-color: #f1f3f5;
      position: sticky;
      top: 0; /* Fixa o título ao rolar */
      z-index: 10;
      border-bottom: 2px solid #ddd;

    }

    .coluna button {
      padding: 10px;
      font-size: 18px;
      cursor: pointer;
      width: 100%;
      white-space: nowrap;
      border: 1px solid #ccc;
      box-sizing: border-box;
      transition: background-color 0.2s ease;
    }

    /* Botões Inputbox */
    .botao-amarelo { background-color: #f0f0f0; color: #000; }
    .botao-verde { background-color: #f0f0f0; color: #000; }
	.botao-lilas { background-color: #f0f0f0; color: #000; }
	.botao-bege { background-color: #f0f0f0; color: #000; }
   
    .botao-amarelo:hover,
    .botao-verde:hover { background-color: #aaaaaa; }
	.botao-lilas:hover { background-color: #aaaaaa; }
	.botao-bege:hover { background-color: #aaaaaa; }
	
	/* Botões Colunas */
	.botao-preto { background-color: #ffffff; color: #000; }
    .botao-vermelho { background-color: #dc3545; color: #ffffff; }
	.botao-preto:hover { background-color: #8c8c8c !important;}
    .botao-vermelho:hover { background-color: #800015 !important; }

    .botoes-chamada {
      display: flex;
      justify-content: center;
      gap: 10px;
      margin-top: 10px;
      margin-bottom: 20px;

    }

    /* Botão voltar ao topo */
   #btn-voltar-topo {
      position: fixed;
      top: 10px;
      right: 100px;
      padding: 10px 20px;
      font-size: 16px;
      background-color: #f1f1f1;
      color: black;
      border: 2px solid #a0a0a0;
      border-radius: 0;
      cursor: pointer;
      z-index: 1000;
      box-shadow: 1px 1px 3px rgba(0, 0, 0, 0.2);
    }

    #btn-voltar-topo:hover {
     background-color: #c0c0c0;
     box-shadow: 2px 2px 6px rgba(0, 0, 0, 0.3);
    }

    #btn-voltar-topo:active {
     background-color: #a0a0a0;
     box-shadow: inset 1px 1px 3px rgba(0, 0, 0, 0.2);
    }

/* Botão voltar fundo */
   #btn-voltar-fundo {
      position: fixed;
      top: 10px;
      right: 10px;
      padding: 10px 20px;
      font-size: 16px;
      background-color: #f1f1f1;
      color: black;
      border: 2px solid #a0a0a0;
      border-radius: 0;
      cursor: pointer;
      z-index: 1000;
      box-shadow: 1px 1px 3px rgba(0, 0, 0, 0.2);
    }

    #btn-voltar-fundo:hover {
     background-color: #c0c0c0;
     box-shadow: 2px 2px 6px rgba(0, 0, 0, 0.3);
    }

    #btn-voltar-fundo:active {
     background-color: #a0a0a0;
     box-shadow: inset 1px 1px 3px rgba(0, 0, 0, 0.2);
    }

/* Botão limpar */
   #btn-limpar {
      position: fixed;
      top: 10px;
      right: 200px;
      padding: 10px 20px;
      font-size: 16px;
      background-color: #ffffff;
      color: black;
      border: 2px solid #a0a0a0;
      border-radius: 0;
      cursor: pointer;
      z-index: 1000;
      box-shadow: 1px 1px 3px rgba(0, 0, 0, 0.2);
    }

    #btn-limpar:hover {
     background-color: #c0c0c0;
     box-shadow: 2px 2px 6px rgba(0, 0, 0, 0.3);
    }

    #btn-limpar:active {
     background-color: #a0a0a0;
     box-shadow: inset 1px 1px 3px rgba(0, 0, 0, 0.2);
    }

    .box-senha {
      position: fixed;
	  display: flex;
      flex-direction: column;
      justify-content: center; /* Alinhamento vertical */
      align-items: center;     /* Alinhamento horizontal */
      left: 20px;
      width: 220px;
	  height: 100px;
      background-color: #ffffff;
      padding: 15px;
      border: 4px solid black;
      border-radius: 0;
      box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.1);
      z-index: 9999;
      margin-top: 20px;
    }

    #box-senha-normal {
      top: 0px;
	  left: 2px;
      color: black;
	 
    }

    #box-senha-preferencial {
      top: 0px;
	  left: 270px;
      background-color: #dc3545;
      color: white;
	
    }

    .box-senha h3 {
      margin-top: 0;
      font-size: 20px;
      text-align: center;
      margin-bottom: 15px;
    }

    .box-senha .senha {
      text-align: center;
      font-size: 18px;
    }

.avisos-container {
  position: fixed;
  top: 20px;
  left: 20px;
  z-index: 1000;
}
  
	.marca-dagua {
  position: fixed;
  top: 70%;
  left: 50%;
  transform: translate(-50%, -50%) rotate(-15deg);
  font-size: 90px;
  color: rgba(0, 0, 0, 0.12); /* transparência leve */
  white-space: nowrap;
  pointer-events: none; /* não interfere em cliques */
  z-index: 0;
  user-select: none;
}

.rodape-fixo {
  position: fixed;
  bottom: 0;
  width: 100%;
  text-align: center;
  font-size: 12px;
  color: gray;
  background-color: transparent;
  padding: 5px 0;
  margin: 0;
  z-index: 9999;
}

.botao-destacado-normal {
  background-color: #dddddd !important; /* cinza claro */
  color: white !important;

}

.botao-destacado-preferencial {
  background-color: #ffc1c1 !important; /* vermelho claro */
  color: white !important;
 
}

#seletor-voz {
  position: fixed;
  top: 125px;
  right: 440px; 
  padding: 8px 12px;
  border-radius: 0px;
  z-index: 1000;
  font-family: Arial, sans-serif;
}


#vozSelecionada {
  font-size: 16px;         /* Tamanho da fonte dentro do select */
  padding: 8px 12px;       /* Espaçamento interno */
  border: 1px solid black;  /* Borda mais visível */
  border-radius: 0px;      /* Cantos arredondados */
  background-color: #fff;  /* Fundo branco */
  margin-left: 0px;       /* Espaço entre label e select */
  max-width: 300px;        /* Largura máxima */
}

label[for="vozSelecionada"] {
  font-size: 16px;         /* Tamanho da fonte do label */
  font-weight: bold;       /* Negrito para destaque */
  font-family: Arial, sans-serif;
}
  </style>

  <script>
    // Oculta o conteúdo até que a verificação seja feita
    if (sessionStorage.getItem("acessoLiberado") !== "true") {
      document.documentElement.style.display = "none";
    }

    document.addEventListener("DOMContentLoaded", function () {
      if (sessionStorage.getItem("acessoLiberado") === "true") {
        document.documentElement.style.display = "block";
      } else {
        document.body.innerHTML = "<h1 style='text-align:center; padding-top:20%; font-family:sans-serif;'>Acesso negado</h1>";
        document.documentElement.style.display = "block";
      }
    });
  </script>
</head>

<body>
  <div class="marca-dagua">Uso Exclusivo da UBS LOPES DE OLIVEIRA</div>

  <h2>CHAMADA DE SENHAS - UBS LOPES DE OLIVEIRA</h2>

  <div class="chamada-nome">
    <input type="text" id="nomePessoa" placeholder="Digite Aqui">
  </div>

<div id="seletor-voz">
  <label for="vozSelecionada">Áudio:</label>
  <select id="vozSelecionada">
    <option value="Microsoft Maria - Portuguese (Brazil)">Feminino</option>
    <option value="Microsoft Daniel - Portuguese (Brazil)">Masculino</option>
  </select>
</div>

  <div class="botoes-chamada">
    <button onclick="chamarNome(1)" class="botao-amarelo">Chamar no Guichê 1</button>
    <button onclick="chamarNome(2)" class="botao-verde">Chamar no Guichê 2</button>
    <button onclick="chamarNome(3)" class="botao-lilas">Chamar no Pós Consulta</button>
    <button onclick="chamarNome(4)" class="botao-bege">Ler em Voz Alta</button>
    <button onclick="exportarChamadasCSV()" class="botao-bege">📄 Gravar Seu Histórico de Chamadas 📄</button>
  </div>

  <div class="grid-container">
    <div class="coluna"><div class="titulo-coluna">Normal<br>Guichê 1</div><div id="coluna-normal-guiche1"></div></div>
    <div class="coluna"><div class="titulo-coluna">Preferencial<br>Guichê 1</div><div id="coluna-preferencial-guiche1"></div></div>
    <div class="coluna"><div class="titulo-coluna">Normal<br>Guichê 2</div><div id="coluna-normal-guiche2"></div></div>
    <div class="coluna"><div class="titulo-coluna">Preferencial<br>Guichê 2</div><div id="coluna-preferencial-guiche2"></div></div>
    <div class="coluna"><div class="titulo-coluna">Normal<br>Pós Consulta</div><div id="coluna-normal-posconsulta"></div></div>
    <div class="coluna"><div class="titulo-coluna">Preferencial<br>Pós Consulta</div><div id="coluna-preferencial-posconsulta"></div></div>
  </div>

  <div class="box-senha" id="box-senha-normal">
    <h3>Sua Última Senha Normal</h3>
    <div class="senha" id="senha-normal">- - - - -</div>
  </div>

  <div class="box-senha" id="box-senha-preferencial">
    <h3>Sua Última Senha Preferencial</h3>
    <div class="senha" id="senha-preferencial">- - - - -</div>
  </div>

  <button id="btn-voltar-topo" onclick="voltarAoTopo()">Início</button>
  <button id="btn-voltar-fundo" onclick="voltarAoFundo()">Fim</button>
  <button id="btn-limpar" onclick="location.reload()">Limpar Senhas</button>

  <footer class="rodape-fixo">
    Desenvolvido por Egalon - Maio 2025 - Versão 0
  </footer>

  <!-- Firebase compat SDK -->
  <script src="https://www.gstatic.com/firebasejs/9.23.0/firebase-app-compat.js"></script>
  <script src="https://www.gstatic.com/firebasejs/9.23.0/firebase-database-compat.js"></script>
  <script>
      const historicoChamadas = [];

  
  function falarVacAdulto() {
  falar("Atenção, para vacinação adulto, tenha em mãos documento com foto");
}

function falarVacInfantil() {
  falar("Atenção, para vacinação infantil, tenha em mãos caderneta de vacinação");
}

function falarRetiradaGuias() {
  falar("Atenção, para retirada de guias, tenha em mãos documento do titular do agendamento");
}

    function voltarAoTopo() {
  const scrollArea = document.querySelector('.grid-container');  // Seleciona a área de rolagem correta
  scrollArea.scrollTo({ top: 0, behavior: 'smooth' });  // Faz o scroll suave até o topo
}

    function voltarAoFundo() {
  const scrollArea = document.querySelector('.grid-container');  // Seleciona a área de rolagem correta
  scrollArea.scrollTo({ top: scrollArea.scrollHeight, behavior: 'smooth' });  // Faz o scroll suave até o topo
}

function carregarVozes(callback) {
  const synth = window.speechSynthesis;

  function tentarCarregar() {
    const vozes = synth.getVoices();
    if (vozes.length > 0) {
      callback(vozes);
    } else {
      // Tenta novamente após um curto intervalo
      setTimeout(tentarCarregar, 100);
    }
  }

  tentarCarregar();
}

function falar(texto) {
  const synth = window.speechSynthesis;
  const msg = new SpeechSynthesisUtterance();
  msg.text = texto;
  msg.lang = 'pt-BR';
  msg.rate = 1.3;

  const vozSelecionada = document.getElementById("vozSelecionada")?.value;

  carregarVozes((vozes) => {
    const voz = vozes.find(v => v.name === vozSelecionada);

    if (voz) {
      msg.voice = voz;
      console.log(`✅ Usando voz: ${voz.name}`);
    } else {
      console.warn(`⚠️ Voz "${vozSelecionada}" não encontrada. Usando voz padrão.`);
    }

    synth.speak(msg);
  });
}



    function chamarNome(guiche) {
  const nome = document.getElementById('nomePessoa').value.trim();
  if (nome === '') {
    alert('Por favor, digite um nome.');
    return;
  }

  let mensagem = '';
  let guicheTexto = '';

  if (guiche === 1) {
    mensagem = `Atenção, ${nome}, dirija-se ao guichê 1`;
    guicheTexto = "Guichê 1";
  } else if (guiche === 2) {
    mensagem = `Atenção, ${nome}, dirija-se ao guichê 2`;
    guicheTexto = "Guichê 2";
  } else if (guiche === 3) {
    mensagem = `Atenção, ${nome}, dirija-se ao pós consulta`;
    guicheTexto = "Pós Consulta";
  } else if (guiche === 4) {
    mensagem = `${nome}`;
    guicheTexto = "Leitura em voz alta";
  }

  // Salva no histórico
  const agora = new Date();
  historicoChamadas.push({
    tipo: "Chamada por nome",
    nome: nome,
    guiche: guicheTexto,
    data: agora.toLocaleDateString('pt-BR'),
    hora: agora.toLocaleTimeString('pt-BR'),
  });

  falar(mensagem);
}


   function atualizarUltimaSenhaNormal(texto) {
  const div = document.getElementById('senha-normal');
  if (div) {
    div.textContent = texto;
  }
}

function atualizarUltimaSenhaPreferencial(texto) {
  const div = document.getElementById('senha-preferencial');
  if (div) {
    div.textContent = texto;
  }
}

 // Objeto para armazenar o último botão clicado por coluna
const ultimosBotoesPorColuna = {};
const maioresSenhasPorColuna = {}; // Armazena o maior número clicado por coluna


function criarBotao(idColuna, texto, classe) {
  const coluna = document.getElementById(idColuna);
  const botao = document.createElement('button');
  botao.textContent = texto;
  botao.className = classe;

  const isPreferencial = idColuna.includes("preferencial");

  // Extrai número da senha (ex: "Senha 008 - Guichê 1" => 8)
  const numeroSenha = parseInt(texto.match(/Senha (\d+)/)[1], 10);

  const destino = texto.split(" - ")[1];
  const textoFalado = isPreferencial
    ? `Senha ${numeroSenha}, preferencial, ${destino}`
    : `Senha ${numeroSenha}, normal, ${destino}`;

  botao.onclick = () => {
    falar(textoFalado);
	
	    // Registrar chamada de senha no histórico
    const agora = new Date();
    historicoChamadas.push({
      tipo: isPreferencial ? "Senha Preferencial" : "Senha Normal",
      senha: texto,
      guiche: destino,
      data: agora.toLocaleDateString('pt-BR'),
      hora: agora.toLocaleTimeString('pt-BR'),
    });


    if (isPreferencial) {
      atualizarUltimaSenhaPreferencial(texto);
    } else {
      atualizarUltimaSenhaNormal(texto);
    }

    const botoesNaColuna = Array.from(coluna.querySelectorAll('button'));

    // Atualiza a maior senha chamada na coluna
    if (
      !maioresSenhasPorColuna[idColuna] ||
      numeroSenha > maioresSenhasPorColuna[idColuna]
    ) {
      maioresSenhasPorColuna[idColuna] = numeroSenha;
    }

    const limite = maioresSenhasPorColuna[idColuna];
    const classeDestaque = isPreferencial
      ? 'botao-destacado-preferencial'
      : 'botao-destacado-normal';

    // Limpa destaques anteriores
    botoesNaColuna.forEach(btn => {
      btn.classList.remove('botao-destacado-normal', 'botao-destacado-preferencial');
    });

    // Destaca todos até o maior número
    botoesNaColuna.forEach(btn => {
      const match = btn.textContent.match(/Senha (\d+)/);
      if (match) {
        const num = parseInt(match[1], 10);
        if (num <= limite) {
          btn.classList.add(classeDestaque);
        }
      }
    });
  };

  coluna.appendChild(botao);
}

    // Criar senhas normais
    for (let i = 1; i <= 999; i++) {
      const numero = i.toString().padStart(1, '0');
      criarBotao("coluna-normal-guiche1", `Senha ${numero} - Guichê 1`, 'botao-preto');
      criarBotao("coluna-normal-guiche2", `Senha ${numero} - Guichê 2`, 'botao-preto');
      criarBotao("coluna-normal-posconsulta", `Senha ${numero} - Pós Consulta`, 'botao-preto');
    }

    // Criar senhas preferenciais
    for (let i = 1; i <= 999; i++) {
      const numero = i.toString().padStart(1, '0');
      criarBotao("coluna-preferencial-guiche1", `Senha ${numero} - Guichê 1`, 'botao-vermelho');
      criarBotao("coluna-preferencial-guiche2", `Senha ${numero} - Guichê 2`, 'botao-vermelho');
      criarBotao("coluna-preferencial-posconsulta", `Senha ${numero} - Pós Consulta`, 'botao-vermelho');
    }
	
function exportarChamadasCSV() {
  if (historicoChamadas.length === 0) {
    alert("Nenhuma chamada registrada.");
    return;
  }

  let csv = "Tipo,Nome/Senha,Guichê,Data,Hora\n";

  historicoChamadas.forEach(registro => {
    const linha = [
      registro.tipo,
      registro.nome || registro.senha || "",
      registro.guiche,
      registro.data,
      registro.hora
    ].map(campo => `"${campo}"`).join(",");
    csv += linha + "\n";
  });

  const blob = new Blob([csv], { type: "text/csv;charset=utf-8;" });
  const url = URL.createObjectURL(blob);
  const link = document.createElement("a");
  link.setAttribute("href", url);
  link.setAttribute("download", "historico_chamadas.csv");
  link.style.visibility = "hidden";
  document.body.appendChild(link);
  link.click();
  document.body.removeChild(link);
}

window.speechSynthesis.onvoiceschanged = () => {
  carregarVozes(() => {});
};


	
 
  </script>
</body>
</html>
