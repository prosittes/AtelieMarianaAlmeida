<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ateliê de Bolos e Doces Mariana Almeida</title>
    <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;600;700&family=Lato:wght@300;400;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --rose-gold: #d4a5a5;
            --chocolate: #5d4037;
            --cream: #faf7f2;
            --gold: #c9a961;
            --dark: #2c1810;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Lato', sans-serif;
            background: var(--cream);
            color: var(--dark);
            overflow-x: hidden;
        }

        /* Header */
        header {
            background: linear-gradient(135deg, var(--rose-gold) 0%, #e8c4c4 100%);
            padding: 2rem 1rem;
            text-align: center;
            position: relative;
            overflow: hidden;
        }

        header::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: radial-gradient(circle, rgba(255,255,255,0.3) 1px, transparent 1px);
            background-size: 20px 20px;
            animation: sparkle 20s linear infinite;
            opacity: 0.5;
        }

        @keyframes sparkle {
            0% { transform: translate(0, 0); }
            100% { transform: translate(20px, 20px); }
        }

        .logo {
            font-family: 'Playfair Display', serif;
            font-size: 2.5rem;
            color: white;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.1);
            position: relative;
            z-index: 1;
        }

        .subtitle {
            font-family: 'Lato', sans-serif;
            font-weight: 300;
            font-size: 1.1rem;
            color: white;
            margin-top: 0.5rem;
            letter-spacing: 3px;
            text-transform: uppercase;
        }

        /* Container */
        .container {
            max-width: 900px;
            margin: 0 auto;
            padding: 2rem 1rem;
        }

        /* Seção do Cardápio */
        .menu-section {
            background: white;
            border-radius: 20px;
            padding: 2.5rem;
            margin-bottom: 2rem;
            box-shadow: 0 10px 40px rgba(93, 64, 55, 0.1);
            position: relative;
            overflow: hidden;
        }

        .menu-section::after {
            content: '🧁';
            position: absolute;
            top: 20px;
            right: 20px;
            font-size: 2rem;
            opacity: 0.2;
        }

        h2 {
            font-family: 'Playfair Display', serif;
            color: var(--chocolate);
            font-size: 1.8rem;
            margin-bottom: 1.5rem;
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }

        .pdf-counter {
            background: var(--rose-gold);
            color: white;
            padding: 0.3rem 0.8rem;
            border-radius: 20px;
            font-size: 0.9rem;
            font-weight: 700;
            margin-left: auto;
        }

        /* Upload de PDF */
        .pdf-upload {
            border: 3px dashed var(--rose-gold);
            border-radius: 15px;
            padding: 2rem;
            text-align: center;
            background: #fff9f9;
            transition: all 0.3s ease;
            cursor: pointer;
            position: relative;
            margin-bottom: 1rem;
        }

        .pdf-upload:hover {
            border-color: var(--chocolate);
            background: #fff5f5;
            transform: translateY(-2px);
        }

        .pdf-upload.dragover {
            border-color: var(--gold);
            background: #fffef5;
            transform: scale(1.02);
        }

        .pdf-upload.disabled {
            opacity: 0.5;
            cursor: not-allowed;
            pointer-events: none;
        }

        .upload-icon {
            font-size: 3rem;
            margin-bottom: 1rem;
        }

        .upload-text {
            color: var(--chocolate);
            font-weight: 600;
            margin-bottom: 0.5rem;
        }

        .upload-hint {
            color: #999;
            font-size: 0.9rem;
        }

        input[type="file"] {
            position: absolute;
            width: 100%;
            height: 100%;
            top: 0;
            left: 0;
            opacity: 0;
            cursor: pointer;
        }

        /* Lista de PDFs */
        .pdf-list {
            display: flex;
            flex-direction: column;
            gap: 0.8rem;
        }

        .pdf-item {
            display: flex;
            align-items: center;
            gap: 1rem;
            padding: 1rem;
            background: linear-gradient(135deg, #f8f9fa 0%, #e9ecef 100%);
            border-radius: 12px;
            border-left: 4px solid var(--rose-gold);
            animation: slideIn 0.3s ease;
            transition: all 0.3s;
        }

        .pdf-item:hover {
            transform: translateX(5px);
            box-shadow: 0 4px 12px rgba(0,0,0,0.1);
        }

        .pdf-number {
            background: var(--chocolate);
            color: white;
            width: 28px;
            height: 28px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 700;
            font-size: 0.85rem;
            flex-shrink: 0;
        }

        .pdf-icon {
            font-size: 1.8rem;
        }

        .pdf-info {
            flex: 1;
            text-align: left;
            min-width: 0;
        }

        .pdf-name {
            font-weight: 700;
            color: var(--chocolate);
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
        }

        .pdf-size {
            font-size: 0.8rem;
            color: #666;
        }

        .remove-pdf {
            background: #ff6b6b;
            color: white;
            border: none;
            padding: 0.5rem 1rem;
            border-radius: 20px;
            cursor: pointer;
            font-size: 0.85rem;
            transition: all 0.2s;
            flex-shrink: 0;
        }

        .remove-pdf:hover {
            background: #ff5252;
            transform: scale(1.05);
        }

        @keyframes slideIn {
            from {
                opacity: 0;
                transform: translateY(-10px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        /* Seção de Sabores */
        .flavors-section {
            background: white;
            border-radius: 20px;
            padding: 2.5rem;
            margin-bottom: 2rem;
            box-shadow: 0 10px 40px rgba(93, 64, 55, 0.1);
        }

        .flavors-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
            gap: 1rem;
            margin-top: 1.5rem;
        }

        .flavor-card {
            border: 2px solid #eee;
            border-radius: 15px;
            padding: 1.5rem 1rem;
            text-align: center;
            cursor: pointer;
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
            position: relative;
            overflow: hidden;
        }

        .flavor-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(135deg, transparent 0%, rgba(255,255,255,0.4) 100%);
            opacity: 0;
            transition: opacity 0.3s;
        }

        .flavor-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 8px 25px rgba(0,0,0,0.1);
        }

        .flavor-card.selected {
            border-color: var(--gold);
            background: linear-gradient(135deg, #fff9e6 0%, #fff5d6 100%);
            transform: scale(1.05);
            box-shadow: 0 8px 25px rgba(201, 169, 97, 0.3);
        }

        .flavor-card.selected::after {
            content: '✓';
            position: absolute;
            top: 8px;
            right: 8px;
            background: var(--gold);
            color: white;
            width: 24px;
            height: 24px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 0.8rem;
            font-weight: bold;
        }

        .flavor-icon {
            font-size: 2.5rem;
            margin-bottom: 0.5rem;
            display: block;
        }

        .flavor-name {
            font-weight: 700;
            color: var(--chocolate);
            font-size: 0.95rem;
        }

        .flavor-desc {
            font-size: 0.8rem;
            color: #888;
            margin-top: 0.3rem;
        }

        /* Formulário de Pedido */
        .order-form {
            background: white;
            border-radius: 20px;
            padding: 2.5rem;
            box-shadow: 0 10px 40px rgba(93, 64, 55, 0.1);
        }

        .form-group {
            margin-bottom: 1.5rem;
        }

        label {
            display: block;
            margin-bottom: 0.5rem;
            color: var(--chocolate);
            font-weight: 600;
            font-size: 0.95rem;
        }

        input[type="text"],
        input[type="tel"],
        textarea,
        select {
            width: 100%;
            padding: 1rem;
            border: 2px solid #e0e0e0;
            border-radius: 12px;
            font-family: 'Lato', sans-serif;
            font-size: 1rem;
            transition: all 0.3s;
            background: #fafafa;
        }

        input:focus,
        textarea:focus,
        select:focus {
            outline: none;
            border-color: var(--rose-gold);
            background: white;
            box-shadow: 0 0 0 3px rgba(212, 165, 165, 0.1);
        }

        textarea {
            resize: vertical;
            min-height: 100px;
        }

        .selected-flavor-display {
            background: linear-gradient(135deg, #fff9e6 0%, #fff5d6 100%);
            border: 2px solid var(--gold);
            border-radius: 12px;
            padding: 1rem;
            margin-bottom: 1.5rem;
            display: none;
            align-items: center;
            gap: 1rem;
            animation: pulse 2s infinite;
        }

        .selected-flavor-display.active {
            display: flex;
        }

        @keyframes pulse {
            0%, 100% { box-shadow: 0 0 0 0 rgba(201, 169, 97, 0.4); }
            50% { box-shadow: 0 0 0 10px rgba(201, 169, 97, 0); }
        }

        .selected-icon {
            font-size: 2rem;
        }

        .selected-text {
            flex: 1;
        }

        .selected-label {
            font-size: 0.85rem;
            color: #888;
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        .selected-name {
            font-weight: 700;
            color: var(--chocolate);
            font-size: 1.1rem;
        }

        /* Botão WhatsApp */
        .whatsapp-btn {
            width: 100%;
            padding: 1.2rem;
            background: linear-gradient(135deg, #25d366 0%, #128c7e 100%);
            color: white;
            border: none;
            border-radius: 50px;
            font-size: 1.1rem;
            font-weight: 700;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 0.8rem;
            transition: all 0.3s;
            box-shadow: 0 4px 15px rgba(37, 211, 102, 0.3);
            position: relative;
            overflow: hidden;
        }

        .whatsapp-btn::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.2), transparent);
            transition: left 0.5s;
        }

        .whatsapp-btn:hover::before {
            left: 100%;
        }

        .whatsapp-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 8px 25px rgba(37, 211, 102, 0.4);
        }

        .whatsapp-btn:active {
            transform: translateY(0);
        }

        .whatsapp-btn:disabled {
            background: #ccc;
            cursor: not-allowed;
            box-shadow: none;
        }

        .whatsapp-icon {
            font-size: 1.5rem;
        }

        /* Footer */
        footer {
            text-align: center;
            padding: 2rem;
            color: var(--chocolate);
            font-size: 0.9rem;
            opacity: 0.8;
        }

        .heart {
            color: var(--rose-gold);
            animation: heartbeat 1.5s ease infinite;
            display: inline-block;
        }

        @keyframes heartbeat {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.2); }
        }

        /* Responsivo */
        @media (max-width: 600px) {
            .logo {
                font-size: 1.8rem;
            }

            .menu-section,
            .flavors-section,
            .order-form {
                padding: 1.5rem;
            }

            .flavors-grid {
                grid-template-columns: repeat(2, 1fr);
            }

            .pdf-item {
                flex-wrap: wrap;
            }

            .pdf-info {
                width: 100%;
                order: 3;
                margin-top: 0.5rem;
            }
        }

        /* Notificação */
        .notification {
            position: fixed;
            top: 20px;
            right: 20px;
            background: var(--chocolate);
            color: white;
            padding: 1rem 1.5rem;
            border-radius: 12px;
            box-shadow: 0 4px 20px rgba(0,0,0,0.2);
            display: none;
            align-items: center;
            gap: 0.8rem;
            z-index: 1000;
            animation: slideInRight 0.3s ease;
        }

        .notification.show {
            display: flex;
        }

        @keyframes slideInRight {
            from {
                transform: translateX(100%);
                opacity: 0;
            }
            to {
                transform: translateX(0);
                opacity: 1;
            }
        }
    </style>
<base target="_blank">
</head>
<body>
    <header>
        <h1 class="logo">Ateliê de Bolos e Doces</h1>
        <p class="subtitle">Mariana Almeida</p>
    </header>

    <div class="container">
        <!-- Seção de Upload do Cardápio - 4 PDFs -->
        <section class="menu-section">
            <h2>
                📋 Seus Cardápios
                <span class="pdf-counter" id="pdfCounter">0/4</span>
            </h2>

            <div class="pdf-upload" id="dropZone">
                <input type="file" id="pdfInput" accept=".pdf" multiple>
                <div class="upload-icon">📁</div>
                <div class="upload-text">Arraste seus cardápios PDF aqui</div>
                <div class="upload-hint">ou clique para selecionar até 4 arquivos</div>
            </div>

            <div class="pdf-list" id="pdfList">
                <!-- PDFs serão inseridos aqui dinamicamente -->
            </div>
        </section>

        <!-- Seção de Sabores de Chocolate -->
        <section class="flavors-section">
            <h2>🍫 Escolha o Sabor do Chocolate</h2>
            <div class="flavors-grid">
                <div class="flavor-card" data-flavor="Ao Leite" onclick="selectFlavor(this)">
                    <span class="flavor-icon">🥛</span>
                    <div class="flavor-name">Ao Leite</div>
                    <div class="flavor-desc">Cremoso e suave</div>
                </div>

                <div class="flavor-card" data-flavor="Meio Amargo" onclick="selectFlavor(this)">
                    <span class="flavor-icon">🍫</span>
                    <div class="flavor-name">Meio Amargo</div>
                    <div class="flavor-desc">Equilíbrio perfeito</div>
                </div>

                <div class="flavor-card" data-flavor="Amargo 70%" onclick="selectFlavor(this)">
                    <span class="flavor-icon">🖤</span>
                    <div class="flavor-name">Amargo 70%</div>
                    <div class="flavor-desc">Intenso e sofisticado</div>
                </div>

                <div class="flavor-card" data-flavor="Branco" onclick="selectFlavor(this)">
                    <span class="flavor-icon">🤍</span>
                    <div class="flavor-name">Branco</div>
                    <div class="flavor-desc">Doce e delicado</div>
                </div>

                <div class="flavor-card" data-flavor="Com Avelã" onclick="selectFlavor(this)">
                    <span class="flavor-icon">🌰</span>
                    <div class="flavor-name">Com Avelã</div>
                    <div class="flavor-desc">Crocante e especial</div>
                </div>

                <div class="flavor-card" data-flavor="Com Café" onclick="selectFlavor(this)">
                    <span class="flavor-icon">☕</span>
                    <div class="flavor-name">Com Café</div>
                    <div class="flavor-desc">Energia e sabor</div>
                </div>
            </div>
        </section>

        <!-- Formulário de Pedido -->
        <section class="order-form">
            <h2>✨ Finalizar Pedido</h2>

            <div class="selected-flavor-display" id="selectedDisplay">
                <span class="selected-icon" id="selectedIcon">🍫</span>
                <div class="selected-text">
                    <div class="selected-label">Sabor Selecionado</div>
                    <div class="selected-name" id="selectedFlavorName">Meio Amargo</div>
                </div>
            </div>

            <div class="form-group">
                <label for="nome">Seu Nome *</label>
                <input type="text" id="nome" placeholder="Digite seu nome completo" required>
            </div>

            <div class="form-group">
                <label for="telefone">WhatsApp *</label>
                <input type="tel" id="telefone" placeholder="(11) 99999-9999" required>
            </div>

            <div class="form-group">
                <label for="quantidade">Quantidade</label>
                <select id="quantidade">
                    <option value="1">1 unidade</option>
                    <option value="2">2 unidades</option>
                    <option value="5">5 unidades</option>
                    <option value="10">10 unidades</option>
                    <option value="outro">Outra quantidade (especificar)</option>
                </select>
            </div>

            <div class="form-group">
                <label for="observacoes">Observações Especiais</label>
                <textarea id="observacoes" placeholder="Alguma preferência especial? Decoração específica? Nos conte!"></textarea>
            </div>

            <button class="whatsapp-btn" onclick="sendToWhatsApp()">
                <span class="whatsapp-icon">💬</span>
                Enviar Pedido pelo WhatsApp
            </button>
        </section>
    </div>

    <footer>
        Feito com <span class="heart">❤</span> por Mariana Almeida
    </footer>

    <div class="notification" id="notification">
        <span>✓</span>
        <span id="notificationText">PDF adicionado!</span>
    </div>

    <script>
        let selectedFlavor = null;
        let selectedFlavorIcon = '🍫';
        let pdfFiles = [];
        const MAX_PDFS = 4;

        // NÚMERO DA MARIANA CONFIGURADO
        const numeroWhatsApp = '5512996733698';

        // Upload de PDF
        const dropZone = document.getElementById('dropZone');
        const pdfInput = document.getElementById('pdfInput');
        const pdfList = document.getElementById('pdfList');
        const pdfCounter = document.getElementById('pdfCounter');

        dropZone.addEventListener('dragover', (e) => {
            e.preventDefault();
            if (pdfFiles.length < MAX_PDFS) {
                dropZone.classList.add('dragover');
            }
        });

        dropZone.addEventListener('dragleave', () => {
            dropZone.classList.remove('dragover');
        });

        dropZone.addEventListener('drop', (e) => {
            e.preventDefault();
            dropZone.classList.remove('dragover');

            const files = Array.from(e.dataTransfer.files).filter(f => f.type === 'application/pdf');
            addPDFs(files);
        });

        pdfInput.addEventListener('change', (e) => {
            if (e.target.files.length > 0) {
                addPDFs(Array.from(e.target.files));
            }
        });

        function addPDFs(newFiles) {
            const availableSlots = MAX_PDFS - pdfFiles.length;

            if (availableSlots <= 0) {
                showNotification('Limite de 4 PDFs atingido!', 'error');
                return;
            }

            const filesToAdd = newFiles.slice(0, availableSlots);

            filesToAdd.forEach(file => {
                pdfFiles.push(file);
                renderPDFItem(file, pdfFiles.length);
            });

            updateCounter();

            if (filesToAdd.length > 0) {
                showNotification(`${filesToAdd.length} PDF(s) adicionado(s)!`);
            }

            if (newFiles.length > availableSlots) {
                showNotification(`${newFiles.length - availableSlots} arquivo(s) ignorado(s) - limite atingido`, 'error');
            }

            pdfInput.value = '';
        }

        function renderPDFItem(file, index) {
            const item = document.createElement('div');
            item.className = 'pdf-item';
            item.id = `pdf-${index}`;
            item.innerHTML = `
                <div class="pdf-number">${index}</div>
                <div class="pdf-icon">📄</div>
                <div class="pdf-info">
                    <div class="pdf-name">${file.name}</div>
                    <div class="pdf-size">${(file.size / 1024).toFixed(1)} KB</div>
                </div>
                <button class="remove-pdf" onclick="removePDF(${index})">Remover</button>
            `;
            pdfList.appendChild(item);
        }

        function removePDF(index) {
            pdfFiles.splice(index - 1, 1);
            refreshPDFList();
            updateCounter();
            showNotification('PDF removido');
        }

        function refreshPDFList() {
            pdfList.innerHTML = '';
            pdfFiles.forEach((file, idx) => {
                renderPDFItem(file, idx + 1);
            });
        }

        function updateCounter() {
            pdfCounter.textContent = `${pdfFiles.length}/${MAX_PDFS}`;

            if (pdfFiles.length >= MAX_PDFS) {
                dropZone.classList.add('disabled');
                dropZone.querySelector('.upload-text').textContent = 'Limite de 4 PDFs atingido';
            } else {
                dropZone.classList.remove('disabled');
                dropZone.querySelector('.upload-text').textContent = 'Arraste seus cardápios PDF aqui';
            }
        }

        // Seleção de Sabor
        function selectFlavor(element) {
            document.querySelectorAll('.flavor-card').forEach(card => {
                card.classList.remove('selected');
            });

            element.classList.add('selected');
            selectedFlavor = element.dataset.flavor;
            selectedFlavorIcon = element.querySelector('.flavor-icon').textContent;

            document.getElementById('selectedDisplay').classList.add('active');
            document.getElementById('selectedFlavorName').textContent = selectedFlavor;
            document.getElementById('selectedIcon').textContent = selectedFlavorIcon;

            showNotification(`Sabor ${selectedFlavor} selecionado!`);
        }

        // Envio para WhatsApp
        function sendToWhatsApp() {
            const nome = document.getElementById('nome').value;
            const telefone = document.getElementById('telefone').value;
            const quantidade = document.getElementById('quantidade').value;
            const observacoes = document.getElementById('observacoes').value;

            if (!nome || !telefone) {
                showNotification('Por favor, preencha seu nome e telefone', 'error');
                return;
            }

            if (!selectedFlavor) {
                showNotification('Por favor, selecione um sabor de chocolate', 'error');
                return;
            }

            let mensagem = `*Novo Pedido - Ateliê Mariana Almeida*%0A%0A`;
            mensagem += `*Cliente:* ${nome}%0A`;
            mensagem += `*Contato:* ${telefone}%0A`;
            mensagem += `*Sabor Escolhido:* ${selectedFlavor}%0A`;
            mensagem += `*Quantidade:* ${quantidade}%0A`;

            if (pdfFiles.length > 0) {
                mensagem += `*Cardápios Anexados:* ${pdfFiles.length} arquivo(s)%0A`;
                pdfFiles.forEach((file, idx) => {
                    mensagem += `  ${idx + 1}. ${file.name}%0A`;
                });
            }

            if (observacoes) {
                mensagem += `*Observações:* ${observacoes}%0A`;
            }

            mensagem += `%0AAguardo confirmação! 😊`;

            const url = `https://wa.me/${numeroWhatsApp}?text=${mensagem}`;
            window.open(url, '_blank');

            showNotification('Redirecionando para o WhatsApp...');
        }

        // Sistema de Notificações
        function showNotification(text, type = 'success') {
            const notification = document.getElementById('notification');
            const notificationText = document.getElementById('notificationText');

            notificationText.textContent = text;
            notification.style.background = type === 'error' ? '#ff6b6b' : 'var(--chocolate)';
            notification.classList.add('show');

            setTimeout(() => {
                notification.classList.remove('show');
            }, 3000);
        }

        // Máscara para telefone
        document.getElementById('telefone').addEventListener('input', function(e) {
            let value = e.target.value.replace(/\D/g, '');
            if (value.length > 11) value = value.slice(0, 11);

            if (value.length > 7) {
                value = `(${value.slice(0,2)}) ${value.slice(2,7)}-${value.slice(7)}`;
            } else if (value.length > 2) {
                value = `(${value.slice(0,2)}) ${value.slice(2)}`;
            } else if (value.length > 0) {
                value = `(${value}`;
            }

            e.target.value = value;
        });
    </script>
</body>
</html>
