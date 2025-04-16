<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <title>Orçamento Inspetor.com</title>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>
  <style>
    body {
      font-family: Arial, sans-serif;
      display: flex;
      justify-content: center;
      background-color: #f5f5f5;
      margin: 0;
      padding: 40px 0;
    }
    .container {
      border: 2px solid #ccc;
      padding: 30px;
      background-color: white;
      width: 90%;
      max-width: 800px;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
    }
    table {
      width: 100%;
      border-collapse: collapse;
      margin-top: 20px;
    }
    th, td {
      padding: 10px;
      border-bottom: 1px solid #ccc;
      text-align: center;
    }
    th {
      background: #f44336;
      color: white;
    }
    button {
      padding: 5px 10px;
      margin: 5px 5px;
    }
    .btn-financeiro, .btn-formalizar {
      padding: 12px 24px;
      font-size: 18px;
      background-color: #4CAF50;
      color: white;
      border: none;
      cursor: pointer;
      margin-top: 20px;
    }
    #totals {
      margin-top: 20px;
      font-size: 18px;
    }
    #descontoStatus {
      margin-top: 20px;
      font-weight: bold;
      color: red;
    }
    #timer, #timerManual {
      font-weight: bold;
      color: blue;
      margin-top: 10px;
    }
    .progress-bar {
      width: 100%;
      background: #eee;
      border-radius: 5px;
      overflow: hidden;
      margin-top: 10px;
    }
    .progress-bar-inner {
      height: 10px;
      background: #4CAF50;
      width: 100%;
      transition: width 1s linear;
    }
    #formularioCadastro {
      margin-top: 30px;
      display: none;
    }
    input {
      padding: 6px;
      width: 100%;
      margin: 5px 0 15px 0;
    }
  </style>
</head>
<body>
<div class="container">
  <h2>Orçamento Inspetor.com</h2>

  <table>
    <thead>
      <tr>
        <th>Dispositivo</th>
        <th>Qtd</th>
        <th>Mensal</th>
        <th>Instalação</th>
      </tr>
    </thead>
    <tbody id="deviceTable"></tbody>
  </table>

  <div id="totals">
    Instalação: <strong id="instalacao">R$ 0,00</strong><br>
    Mensalidade: <strong id="mensalidade">R$ 0,00</strong>
  </div>

  <br>
  <button id="btnDesconto" onclick="solicitarDesconto()">Solicitar Desconto</button>
  <div id="descontoStatus"></div>
  <div id="timer"></div>
  <div id="timerManual"></div>

  <div id="formularioCadastro">
    <h3>Dados Cadastrais</h3>
    <input type="text" id="cnpjInput" placeholder="CNPJ">
    <input type="text" id="nomeInput" placeholder="Nome do Cliente">
    <input type="text" id="emailInput" placeholder="Email">
    <input type="text" id="telefoneInput" placeholder="Telefone">
    <button class="btn-formalizar" onclick="gerarPDF()">Formalizar Proposta</button>
  </div>
</div>

<script>
  let cnpjCliente = '';

  let devices = [
    { nome: "Proteção Patrimonial", install: 897, monthly: 199, qtd: 1, fixed: true },
    { nome: "Comunicação GPRS", install: 0, monthly: 40, qtd: 0 },
    { nome: "Sensor Presença Interno", install: 0, monthly: 12, qtd: 0 },
    { nome: "Sensor de Abertura", install: 0, monthly: 10, qtd: 0 },
    { nome: "Sensor Presença Externo", install: 0, monthly: 20, qtd: 0 },
    { nome: "Monitor Piso Ferro", install: 0, monthly: 20, qtd: 0 },
    { nome: "Teclado Alfanumérico", install: 0, monthly: 15, qtd: 0 },
    { nome: "Controle Remoto/Pânico", install: 0, monthly: 10, qtd: 0 },
    { nome: "Câmera Full HD", install: 137, monthly: 45, qtd: 0 }
  ];

  const descontos = [
    { install: 699, monthly: 199 },
    { install: 0, monthly: 40 },
    { install: 0, monthly: 9 },
    { install: 0, monthly: 9 },
    { install: 0, monthly: 12 },
    { install: 0, monthly: 15 },
    { install: 0, monthly: 10 },
    { install: 0, monthly: 5 },
    { install: 120, monthly: 40 }
  ];

  function renderTable() {
    let html = '';
    devices.forEach((d, i) => {
      html += `<tr>
        <td>${d.nome}</td>
        <td>
          ${d.fixed ? d.qtd : `
          <button onclick="alterarQtd(${i}, -1)">-</button>
          ${d.qtd}
          <button onclick="alterarQtd(${i}, 1)">+</button>`}
        </td>
        <td>R$ ${d.monthly}</td>
        <td>${d.install > 0 ? `R$ ${d.install}` : '-'}</td>
      </tr>`;
    });
    document.getElementById('deviceTable').innerHTML = html;
    calcularTotais();
  }

  function alterarQtd(index, delta) {
    let d = devices[index];
    d.qtd = Math.max(0, d.qtd + delta);
    renderTable();
  }

  function calcularTotais() {
    let totalInstall = 0;
    let totalMonthly = 0;
    devices.forEach(d => {
      totalInstall += d.qtd * d.install;
      totalMonthly += d.qtd * d.monthly;
    });
    document.getElementById('instalacao').textContent = `R$ ${(totalInstall/3).toFixed(2)} x3`;
    document.getElementById('mensalidade').textContent = `R$ ${totalMonthly.toFixed(2)}`;
  }

  function solicitarDesconto() {
    cnpjCliente = prompt("Informe o CNPJ do cliente:");
    if (!cnpjCliente) return;
    document.getElementById('cnpjInput').value = cnpjCliente;
    document.getElementById('descontoStatus').textContent = '';
    document.getElementById('btnDesconto').disabled = true;

    iniciarTimer(15, () => {
      document.getElementById('descontoStatus').textContent = "Desconto não concedido para o CNPJ informado.";
      document.getElementById('timer').innerHTML = `<button class="btn-financeiro" onclick="solicitarAnaliseManual()">Solicitar Análise Financeiro</button>`;
    }, 0);
  }

  function solicitarAnaliseManual() {
    document.getElementById('timer').textContent = '';
    iniciarTimer(180, aplicarDesconto, 60, true);
  }

  function iniciarTimer(duration, callback, interruptAt, showBar = false) {
    let remaining = duration;
    const label = duration > 60 ? 'timerManual' : 'timer';
    const el = document.getElementById(label);

    let progressBarHTML = '';
    if (showBar) {
      progressBarHTML = `<div class="progress-bar"><div class="progress-bar-inner" id="progressBar"></div></div>`;
      el.innerHTML = progressBarHTML;
    }

    const interval = setInterval(() => {
      remaining--;
      if (showBar) {
        let percent = (remaining / duration) * 100;
        document.getElementById('progressBar').style.width = percent + '%';
      }
      el.innerHTML = (showBar ? progressBarHTML : '') + `<div style="margin-top:5px;">Aguardando análise... ${remaining}s</div>`;
      if (remaining <= interruptAt) {
        clearInterval(interval);
        el.innerHTML = '';
        callback();
      }
    }, 1000);
  }

  function aplicarDesconto() {
    document.getElementById('descontoStatus').innerHTML = "<strong style='color: green;'>Desconto concedido manualmente por diretor comercial.</strong>";
    document.getElementById('btnDesconto').style.display = 'none';
    devices = devices.map((d, i) => ({
      ...d,
      install: descontos[i].install,
      monthly: descontos[i].monthly
    }));
    renderTable();
    document.getElementById('formularioCadastro').style.display = 'block';
  }

  function gerarPDF() {
    const { jsPDF } = window.jspdf;
    const doc = new jsPDF();

    const nome = document.getElementById('nomeInput').value;
    const cnpj = document.getElementById('cnpjInput').value;
    const email = document.getElementById('emailInput').value;
    const tel = document.getElementById('telefoneInput').value;

    let totalInstall = 0;
    let totalMonthly = 0;

    let y = 10;
    doc.setFontSize(14);
    doc.text("Proposta Comercial - Inspetor.com", 15, y += 10);
    doc.setFontSize(10);
    doc.text(`Nome: ${nome}`, 15, y += 8);
    doc.text(`CNPJ: ${cnpj}`, 15, y += 6);
    doc.text(`Email: ${email}`, 15, y += 6);
    doc.text(`Telefone: ${tel}`, 15, y += 6);

    y += 10;
    doc.setFontSize(12);
    doc.text("Serviço de Proteção Patrimonial inclui:", 15, y += 8);
    doc.setFontSize(10);
    const beneficios = [
      "Monitoramento 24h do local acionado",
      "Visualização do local monitorado em tempo real",
      "Escuta no local monitorado em tempo real",
      "Controle total via aplicativo",
      "Garantia contínua dos equipamentos",
      "Manutenção e visita técnica",
      "Alteração de projeto sem custo",
      "Suporte técnico 24h",
      "Ronda tática presencial"
    ];
    beneficios.forEach(item => {
      doc.text(`✔ ${item}`, 18, y += 6);
    });

    y += 10;
    doc.setFontSize(12);
    doc.text("Dispositivos de Segurança", 15, y += 10);
    doc.setFontSize(10);
    devices.forEach(d => {
      if (d.qtd > 0) {
        const linha = `${d.nome} | Qtd: ${d.qtd} | Instalação: R$ ${d.install} | Mensal: R$ ${d.monthly}`;
        doc.text(linha, 15, y += 6);
        totalInstall += d.qtd * d.install;
        totalMonthly += d.qtd * d.monthly;
      }
    });

    y += 10;
    doc.setFontSize(11);
    doc.text(`Investimento Instalação: R$ ${(totalInstall/3).toFixed(2)} x3`, 15, y += 8);
    doc.text(`Monitoramento e Suporte 24h: R$ ${totalMonthly.toFixed(2)}`, 15, y += 6);

    y += 20;
    doc.text("Assinatura do Cliente: ___________________________", 15, y);
    doc.text("INSPETOR.COM - 11.818.488/0001-85", 15, y + 10);

    doc.save("proposta_inspetor.pdf");
  }

  renderTable();
</script>
</body>
</html>
