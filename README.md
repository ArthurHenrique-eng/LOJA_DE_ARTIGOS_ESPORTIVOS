# LOJA_DE_ARTIGOS_ESPORTIVOS
Site direcionado a venda de produtos esportivos de todas as marcas


<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Loja de Artigos de Esporte</title>
    <style>
        /* ======== RESET E CONFIGURAÇÕES GERAIS ======== */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: "Poppins", Arial, sans-serif;
        }

        body {
            background: linear-gradient(135deg, #0099ff, #00cc88);
            display: flex;
            justify-content: center;
            align-items: flex-start;
            min-height: 100vh;
            padding: 40px;
            color: #333;
        }

        /* ======== CONTAINER PRINCIPAL ======== */
        .container {
            background: #fff;
            border-radius: 12px;
            box-shadow: 0 8px 20px rgba(0, 0, 0, 0.2);
            padding: 40px;
            width: 100%;
            max-width: 900px;
            animation: fadeIn 1s ease-in-out;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(-20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        /* ======== TÍTULOS ======== */
        h1, h2, h3 {
            text-align: center;
            margin-bottom: 20px;
        }

        h1 {
            font-size: 28px;
            color: #0066cc;
        }

        h3 {
            font-size: 18px;
            color: #333;
            margin-bottom: 30px;
        }

        /* ======== FORMULÁRIOS ======== */
        form {
            display: flex;
            flex-direction: column;
            gap: 15px;
        }

        label {
            font-weight: 600;
            margin-bottom: 5px;
            color: #333;
        }

        input, select {
            width: 100%;
            padding: 12px;
            border: 1px solid #ccc;
            border-radius: 6px;
            font-size: 16px;
            transition: all 0.3s ease;
        }

        input:focus, select:focus {
            border-color: #00cc88;
            outline: none;
            box-shadow: 0 0 6px rgba(0, 204, 136, 0.5);
        }

        /* ======== BOTÕES ======== */
        button {
            background-color: #00cc88;
            color: #fff;
            padding: 12px;
            border: none;
            border-radius: 6px;
            font-size: 16px;
            font-weight: bold;
            cursor: pointer;
            transition: 0.3s;
        }

        button:hover {
            background-color: #009966;
            transform: scale(1.03);
        }

        button a {
            color: white;
            text-decoration: none;
        }

        /* ======== SESSÕES ======== */
        .section {
            background: #f9f9f9;
            padding: 25px;
            border-radius: 8px;
            margin-bottom: 40px;
        }

        .section-title {
            text-align: center;
            font-size: 22px;
            color: #0066cc;
            margin-bottom: 20px;
        }

        /* ======== TABELA ======== */
        table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 15px;
            border-radius: 6px;
            overflow: hidden;
        }

        th, td {
            padding: 12px;
            border: 1px solid #ddd;
            text-align: center;
        }

        thead {
            background-color: #00cc88;
            color: white;
        }

        tbody tr:nth-child(even) {
            background-color: #f2f2f2;
        }

        tbody tr:hover {
            background-color: #e0f7fa;
        }

        .btn-editar, .btn-excluir {
            border: none;
            padding: 8px 12px;
            border-radius: 5px;
            color: white;
            cursor: pointer;
            transition: 0.3s;
            font-size: 14px;
        }

        .btn-editar {
            background-color: #0066cc;
        }

        .btn-editar:hover {
            background-color: #004c99;
        }

        .btn-excluir {
            background-color: #ff5555;
        }

        .btn-excluir:hover {
            background-color: #cc0000;
        }

        /* ======== RODAPÉ ======== */
        footer {
            margin-top: 30px;
            text-align: center;
            font-size: 14px;
            color: #555;
        }

        /* ======== RESPONSIVIDADE ======== */
        @media (max-width: 768px) {
            .container {
                padding: 25px;
            }

            table {
                font-size: 13px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- Seção de Login -->
        <section class="section" id="login-section">
            <h1>Bem-vindo à Nossa Loja de Artigos de Esporte!</h1>
            <h3>Acesse o sistema da loja</h3>

            <form action="login" method="post">
                <label for="username">Usuário:</label>
                <input type="text" id="username" name="username" required>

                <label for="password">Senha:</label>
                <input type="password" id="password" name="password" required>

                <button type="button" onclick="mostrarCadastro()">Entrar</button>
            </form>
        </section>

        <!-- Seção de Cadastro de Produtos -->
        <section class="section" id="cadastro-section" style="display: none;">
            <h2 class="section-title">Cadastro de Produtos</h2>
            <form id="form-produto">
                <label for="produto">Produto:</label>
                <input type="text" id="produto" name="produto" placeholder="Ex: Camisa Nike" required>

                <label for="categoria">Categoria:</label>
                <select id="categoria" required>
                    <option value="">-- Selecione a Categoria --</option>
                    <option value="Camisa">Camisa</option>
                    <option value="Short">Short</option>
                    <option value="Calçado">Calçado</option>
                    <option value="Bermuda">Bermuda</option>
                </select>

                <label for="valor">Preço (R$):</label>
                <input type="number" id="valor" name="valor" step="0.01" min="0" placeholder="Ex: 199.90" required>

                <button type="submit">Cadastrar Produto</button>
            </form>

            <!-- Tabela de Produtos -->
            <table>
                <thead>
                    <tr>
                        <th>Produto</th>
                        <th>Categoria</th>
                        <th>Preço (R$)</th>
                        <th>Ações</th>
                    </tr>
                </thead>
                <tbody id="tabela-produtos">
                    <tr>
                        <td>Camisa Nike</td>
                        <td>Camisa</td>
                        <td>129,99</td>
                        <td>
                            <button class="btn-editar">Editar</button>
                            <button class="btn-excluir">Excluir</button>
                        </td>
                    </tr>
                </tbody>
            </table>
        </section>

        <footer>© 2025 Loja de Esportes. Todos os direitos reservados.</footer>
    </div>

    <script>
        // Função para alternar entre login e cadastro
        function mostrarCadastro() {
            document.getElementById('login-section').style.display = 'none';
            document.getElementById('cadastro-section').style.display = 'block';
        }

        // Função simples para adicionar produto na tabela
        document.getElementById('form-produto').addEventListener('submit', function(event) {
            event.preventDefault();

            const nome = document.getElementById('produto').value;
            const categoria = document.getElementById('categoria').value;
            const valor = document.getElementById('valor').value;

            if (nome && categoria && valor) {
                const tabela = document.getElementById('tabela-produtos');
                const novaLinha = document.createElement('tr');

                novaLinha.innerHTML = `
                    <td>${nome}</td>
                    <td>${categoria}</td>
                    <td>${parseFloat(valor).toFixed(2)}</td>
                    <td>
                        <button class="btn-editar">Editar</button>
                        <button class="btn-excluir">Excluir</button>
                    </td>
                `;

                tabela.appendChild(novaLinha);

                // Limpar campos
                document.getElementById('form-produto').reset();
            }
        });
    </script>
</body>
</html>
