<!DOCTYPE html>
<html lang="pt">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes">
  <title>Gestão de Alunos - TLP | IMCL</title>
  <style>
    * {
      box-sizing: border-box;
      font-family: system-ui, 'Segoe UI', 'Roboto', 'Poppins', sans-serif;
    }

    body {
      background: #f0f7ff;
      margin: 0;
      padding: 24px 16px;
      color: #1e2a3e;
    }

    .container {
      max-width: 1400px;
      margin: 0 auto;
    }

    /* cabeçalho */
    .header {
      text-align: center;
      margin-bottom: 28px;
    }

    .header h1 {
      font-size: 1.9rem;
      background: linear-gradient(135deg, #1e3c72, #2b4c8a);
      background-clip: text;
      -webkit-background-clip: text;
      color: transparent;
      margin: 0 0 6px 0;
    }

    .header p {
      color: #2c5a8c;
      font-weight: 500;
      border-bottom: 2px solid #cbdff2;
      display: inline-block;
      padding-bottom: 6px;
    }

    /* formulário */
    .form-card {
      background: white;
      border-radius: 32px;
      box-shadow: 0 12px 28px rgba(0, 0, 0, 0.08);
      padding: 20px 24px;
      margin-bottom: 32px;
      transition: all 0.2s;
      border: 1px solid #e2edf7;
    }

    .form-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
      gap: 16px 20px;
      margin-bottom: 20px;
    }

    .input-group {
      display: flex;
      flex-direction: column;
      gap: 6px;
    }

    .input-group label {
      font-weight: 600;
      font-size: 0.8rem;
      text-transform: uppercase;
      letter-spacing: 0.5px;
      color: #2c5a8c;
    }

    .input-group input, .input-group select {
      padding: 10px 12px;
      border: 1px solid #cbdbe6;
      border-radius: 20px;
      font-size: 0.9rem;
      background: #fefefe;
      transition: 0.2s;
    }

    .input-group input:focus {
      outline: none;
      border-color: #1e6fdf;
      box-shadow: 0 0 0 2px rgba(30, 111, 223, 0.2);
    }

    .double-btns {
      display: flex;
      gap: 16px;
      justify-content: flex-end;
      flex-wrap: wrap;
    }

    button {
      background: #1e6fdf;
      border: none;
      padding: 10px 24px;
      border-radius: 40px;
      font-weight: bold;
      color: white;
      font-size: 0.9rem;
      cursor: pointer;
      transition: background 0.2s, transform 0.1s;
      box-shadow: 0 2px 5px rgba(0,0,0,0.1);
    }

    button:hover {
      background: #0f5bc0;
      transform: scale(0.98);
    }

    .btn-secondary {
      background: #6c757d;
    }

    .btn-secondary:hover {
      background: #49555f;
    }

    /* tabela responsiva */
    .table-wrapper {
      overflow-x: auto;
      border-radius: 24px;
      background: white;
      box-shadow: 0 6px 18px rgba(0,0,0,0.05);
      border: 1px solid #dee9f2;
    }

    table {
      width: 100%;
      border-collapse: collapse;
      font-size: 0.8rem;
      min-width: 1200px;
    }

    th {
      background: #eef3fc;
      color: #1e4663;
      padding: 14px 8px;
      font-weight: 700;
      border-bottom: 2px solid #cbdbe6;
      text-align: center;
    }

    td {
      padding: 10px 6px;
      text-align: center;
      border-bottom: 1px solid #e2edf2;
      vertical-align: middle;
    }

    tr:hover td {
      background: #f9fcff;
    }

    .badge {
      display: inline-block;
      padding: 4px 12px;
      border-radius: 40px;
      font-weight: bold;
      font-size: 0.75rem;
    }

    .apto { background: #c8f0d1; color: #146b3a; }
    .napto { background: #ffe0db; color: #b13e2d; }
    .recurso { background: #fff0c0; color: #a86f1c; }

    .footer {
      margin-top: 28px;
      text-align: center;
      font-size: 0.75rem;
      color: #547c9e;
    }

    @media (max-width: 760px) {
      .form-grid { grid-template-columns: 1fr; }
      .header h1 { font-size: 1.5rem; }
      th, td { font-size: 0.7rem; padding: 8px 4px; }
    }
  </style>
</head>
<body>
<div class="container">
  <div class="header">
    <h1>📋 Sistema de Avaliação - TLP</h1>
    <p>IMCL | Informática de Gestão | Turma ANI - 12° Classe</p>
  </div>

  <!-- FORMULÁRIO DE CADASTRO -->
  <div class="form-card">
    <h3 style="margin-top: 0; display: flex; align-items: center; gap: 8px;">📝 Novo Aluno</h3>
    <div class="form-grid" id="formGrid">
      <div class="input-group"><label>Escola</label><input type="text" id="escola" value="IMCL" placeholder="Escola"></div>
      <div class="input-group"><label>Curso</label><input type="text" id="curso" value="Informática De Gestão" placeholder="Curso"></div>
      <div class="input-group"><label>Nome completo</label><input type="text" id="nome" placeholder="Ex: Cândido Alfredo"></div>
      <div class="input-group"><label>Nº do Aluno</label><input type="text" id="numero" placeholder="Número"></div>
      <div class="input-group"><label>Nº do BI</label><input type="text" id="bi" placeholder="BI"></div>
      <div class="input-group"><label>Telefone</label><input type="tel" id="telefone" placeholder="+244 9xx xxx xxx"></div>
      <div class="input-group"><label>E-mail</label><input type="email" id="email" placeholder="exemplo@mail.com"></div>
      <div class="input-group"><label>Turma</label><input type="text" id="turma" value="ANI" placeholder="Turma"></div>
      <div class="input-group"><label>Turno</label><input type="text" id="turno" value="Noite" placeholder="Turno"></div>
      <div class="input-group"><label>Classe</label><input type="text" id="classe" value="12°" placeholder="Classe"></div>
      <div class="input-group"><label>Disciplina</label><input type="text" id="disciplina" value="TLP" placeholder="Disciplina"></div>
      <div class="input-group"><label>Nota MAC (0-20)</label><input type="number" id="notaMac" step="0.1" min="0" max="20" value="14"></div>
      <div class="input-group"><label>Nota Prova Professor</label><input type="number" id="notaProf" step="0.1" min="0" max="20" value="12"></div>
      <div class="input-group"><label>Nota Prova Escola</label><input type="number" id="notaEscola" step="0.1" min="0" max="20" value="13"></div>
    </div>
    <div class="double-btns">
      <button type="button" class="btn-secondary" id="limparFormBtn">🧹 Limpar campos</button>
      <button type="button" id="adicionarBtn">➕ Adicionar Aluno à Tabela</button>
    </div>
  </div>

  <!-- TABELA COM TODOS OS DADOS -->
  <div class="table-wrapper">
    <table id="tabelaAlunos">
      <thead>
        <tr>
          <th>Escola</th><th>Curso</th><th>Nome</th><th>Nº</th><th>BI</th><th>Telefone</th><th>Email</th>
          <th>Turma</th><th>Turno</th><th>Classe</th><th>Disciplina</th>
          <th>MAC</th><th>Prova Prof</th><th>Prova Escola</th><th>Média</th><th>Condição</th>
        </tr>
      </thead>
      <tbody id="tabelaBody">
        <!-- linhas inseridas via JS (alunos iniciais + novos) -->
      </tbody>
    </table>
  </div>
  <div class="footer">
    💡 Condição: Média ≥ 12 → <strong>Apto</strong> | Média entre 10 e 11.9 → <strong>Recurso</strong> | Média < 10 → <strong>N/Apto</strong>
  </div>
</div>

<script>
  //  -----  LÓGICA DE MÉDIA E CONDIÇÃO  -----
  function calcularMedia(notaMAC, notaProf, notaEscola) {
    return (notaMAC + notaProf + notaEscola) / 3;
  }

  function obterCondicao(media) {
    if (media >= 12) return "Apto";
    if (media >= 10 && media < 12) return "Recurso";
    return "N/Apto";
  }

  // formatação da média (1 casa decimal)
  function formatMedia(media) {
    return media.toFixed(1);
  }

  // classe CSS para estilização da badge
  function classeCondicao(condicao) {
    if (condicao === "Apto") return "apto";
    if (condicao === "Recurso") return "recurso";
    return "napto";
  }

  // função principal: adicionar uma linha na tabela (sem duplicar referências)
  function adicionarLinhaTabela(aluno) {
    const tbody = document.getElementById("tabelaBody");
    const media = aluno.media;
    const condicao = aluno.condicao;
    const mediaFormatada = formatMedia(media);
    const badgeClass = classeCondicao(condicao);

    const novaLinha = document.createElement("tr");

    // montar células exatamente na ordem do thead
    novaLinha.innerHTML = `
      <td>${escapeHtml(aluno.escola)}</td>
      <td>${escapeHtml(aluno.curso)}</td>
      <td>${escapeHtml(aluno.nome)}</td>
      <td>${escapeHtml(aluno.numero)}</td>
      <td>${escapeHtml(aluno.bi)}</td>
      <td>${escapeHtml(aluno.telefone)}</td>
      <td>${escapeHtml(aluno.email)}</td>
      <td>${escapeHtml(aluno.turma)}</td>
      <td>${escapeHtml(aluno.turno)}</td>
      <td>${escapeHtml(aluno.classe)}</td>
      <td>${escapeHtml(aluno.disciplina)}</td>
      <td>${aluno.notaMAC}</td>
      <td>${aluno.notaProf}</td>
      <td>${aluno.notaEscola}</td>
      <td><strong>${mediaFormatada}</strong></td>
      <td><span class="badge ${badgeClass}">${condicao}</span></td>
    `;
    tbody.appendChild(novaLinha);
  }

  // utilitário anti-XSS
  function escapeHtml(str) {
    if (!str) return "";
    return str.replace(/[&<>]/g, function(m) {
      if (m === '&') return '&amp;';
      if (m === '<') return '&lt;';
      if (m === '>') return '&gt;';
      return m;
    }).replace(/[\uD800-\uDBFF][\uDC00-\uDFFF]/g, function(c) {
      return c;
    });
  }

  // Obter dados do formulário e validar
  function coletarDadosFormulario() {
    const escola = document.getElementById("escola").value.trim();
    const curso = document.getElementById("curso").value.trim();
    const nome = document.getElementById("nome").value.trim();
    const numero = document.getElementById("numero").value.trim();
    const bi = document.getElementById("bi").value.trim();
    const telefone = document.getElementById("telefone").value.trim();
    const email = document.getElementById("email").value.trim();
    const turma = document.getElementById("turma").value.trim();
    const turno = document.getElementById("turno").value.trim();
    const classe = document.getElementById("classe").value.trim();
    const disciplina = document.getElementById("disciplina").value.trim();
    
    let notaMac = parseFloat(document.getElementById("notaMac").value);
    let notaProf = parseFloat(document.getElementById("notaProf").value);
    let notaEscola = parseFloat(document.getElementById("notaEscola").value);

    // validações
    if (!nome || !numero || !bi || !telefone || !email || !turma || !disciplina) {
      alert("❌ Por favor, preencha todos os campos obrigatórios: Nome, Nº, BI, Telefone, Email, Turma e Disciplina.");
      return null;
    }
    if (isNaN(notaMac) || isNaN(notaProf) || isNaN(notaEscola)) {
      alert("⚠️ As notas devem ser números válidos.");
      return null;
    }
    if (notaMac < 0 || notaMac > 20 || notaProf < 0 || notaProf > 20 || notaEscola < 0 || notaEscola > 20) {
      alert("📏 As notas devem estar entre 0 e 20.");
      return null;
    }
    // arredondar para 1 casa decimal para consistência
    notaMac = Math.round(notaMac * 10) / 10;
    notaProf = Math.round(notaProf * 10) / 10;
    notaEscola = Math.round(notaEscola * 10) / 10;

    const media = calcularMedia(notaMac, notaProf, notaEscola);
    const condicao = obterCondicao(media);

    return {
      escola: escola || "IMCL",
      curso: curso || "Informática De Gestão",
      nome, numero, bi, telefone, email, turma, turno: turno || "Noite",
      classe: classe || "12°", disciplina: disciplina || "TLP",
      notaMAC: notaMac, notaProf: notaProf, notaEscola: notaEscola,
      media: media, condicao: condicao
    };
  }

  // função para limpar formulário (apenas os campos editáveis, sem perder padrões)
  function limparFormulario() {
    document.getElementById("nome").value = "";
    document.getElementById("numero").value = "";
    document.getElementById("bi").value = "";
    document.getElementById("telefone").value = "";
    document.getElementById("email").value = "";
    document.getElementById("turma").value = "ANI";
    document.getElementById("turno").value = "Noite";
    document.getElementById("classe").value = "12°";
    document.getElementById("disciplina").value = "TLP";
    document.getElementById("notaMac").value = "14";
    document.getElementById("notaProf").value = "12";
    document.getElementById("notaEscola").value = "13";
    // escola e curso mantém os padrões IMCL e Informática de Gestão, mas não apagamos
    document.getElementById("escola").value = "IMCL";
    document.getElementById("curso").value = "Informática De Gestão";
  }

  // ADICIONAR via botão (interligação formulário -> tabela)
  function adicionarDoFormulario() {
    const alunoData = coletarDadosFormulario();
    if (alunoData) {
      adicionarLinhaTabela(alunoData);
      // opcional: dar scroll suave para a tabela
      document.querySelector(".table-wrapper").scrollIntoView({ behavior: "smooth", block: "nearest" });
      // limpar somente campos de nome, numero, bi, telefone, email (para facilitar próximo cadastro)
      // mas mantém notas padrão? melhor limpar completamente exceto dados institucionais.
      document.getElementById("nome").value = "";
      document.getElementById("numero").value = "";
      document.getElementById("bi").value = "";
      document.getElementById("telefone").value = "";
      document.getElementById("email").value = "";
      // redefinir notas para valores neutros (opcional)
      document.getElementById("notaMac").value = "10";
      document.getElementById("notaProf").value = "10";
      document.getElementById("notaEscola").value = "10";
      // foco no nome
      document.getElementById("nome").focus();
    }
  }

  // ---------- DADOS INICIAIS: O ALUNO FORNECIDO + 4 ALUNOS ADICIONAIS ----------
  const alunosIniciais = [
    { // 1) Cândido General Alfredo (dados reais)
      escola: "IMCL", curso: "Informática De Gestão", nome: "Cândido General Alfredo",
      numero: "08", bi: "020491615LA054", telefone: "926222594", email: "candidoalfredo128@gmail.com",
      turma: "ANI", turno: "Noite", classe: "12°", disciplina: "TLP",
      notaMAC: 14, notaProf: 12, notaEscola: 13
    },
    { // 2) Maria Silva (Recurso)
      escola: "IMCL", curso: "Informática De Gestão", nome: "Maria Luísa Silva",
      numero: "10", bi: "123456789LA001", telefone: "911111111", email: "maria.silva@estudante.imcl.ao",
      turma: "ANI", turno: "Noite", classe: "12°", disciplina: "TLP",
      notaMAC: 10, notaProf: 11, notaEscola: 9
    },
    { // 3) João Manuel (N/Apto)
      escola: "IMCL", curso: "Informática De Gestão", nome: "João Manuel C. Ferreira",
      numero: "15", bi: "789012345LA002", telefone: "922222222", email: "joao.ferreira@imcl.ao",
      turma: "ANI", turno: "Noite", classe: "12°", disciplina: "TLP",
      notaMAC: 8, notaProf: 7, notaEscola: 6
    },
    { // 4) Ana Paula (Apto - alta performance)
      escola: "IMCL", curso: "Informática De Gestão", nome: "Ana Paula Monteiro",
      numero: "22", bi: "345678901LA003", telefone: "933333333", email: "ana.monteiro@estudante.ao",
      turma: "ANI", turno: "Noite", classe: "12°", disciplina: "TLP",
      notaMAC: 15, notaProf: 16, notaEscola: 17
    },
    { // 5) Carlos Mendes (Apto médio)
      escola: "IMCL", curso: "Informática De Gestão", nome: "Carlos Eduardo Mendes",
      numero: "30", bi: "456789123LA004", telefone: "944444444", email: "carlos.mendes@imcl.ao",
      turma: "ANI", turno: "Noite", classe: "12°", disciplina: "TLP",
      notaMAC: 13, notaProf: 12, notaEscola: 14
    }
  ];

  // Preencher tabela com os 5 alunos, já calculando media e condição
  function carregarAlunosIniciais() {
    const tbody = document.getElementById("tabelaBody");
    tbody.innerHTML = ""; // limpa qualquer linha de exemplo
    for (let aluno of alunosIniciais) {
      const media = calcularMedia(aluno.notaMAC, aluno.notaProf, aluno.notaEscola);
      const condicao = obterCondicao(media);
      const alunoCompleto = {
        ...aluno,
        media: media,
        condicao: condicao
      };
      adicionarLinhaTabela(alunoCompleto);
    }
  }

  // Eventos e inicialização
  document.addEventListener("DOMContentLoaded", () => {
    carregarAlunosIniciais();

    const addBtn = document.getElementById("adicionarBtn");
    const limparBtn = document.getElementById("limparFormBtn");

    addBtn.addEventListener("click", adicionarDoFormulario);
    limparBtn.addEventListener("click", limparFormulario);

    // Opção extra: tecla Enter no formulário (adicionar)
    const camposForm = document.querySelectorAll("#formGrid input");
    camposForm.forEach(campo => {
      campo.addEventListener("keypress", (e) => {
        if (e.key === "Enter") {
          e.preventDefault();
          adicionarDoFormulario();
        }
      });
    });
  });
</script>
</body>
</html>
