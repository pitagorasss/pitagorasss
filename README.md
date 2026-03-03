<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pipeline de Dados • ETL • Vendas • Gestão Comercial</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Inter', 'SF Pro Display', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
            background: #0b0f1a;
            line-height: 1.6;
            padding: 0;
            min-height: 100vh;
            color: #e2e8f0;
        }
        
        /* Hero Section Aprimorada */
        .hero {
            background: #0b0f1a;
            padding: 100px 20px 120px;
            position: relative;
            overflow: hidden;
            border-bottom: 1px solid rgba(129, 140, 248, 0.2);
        }
        
        /* Background com efeito de ondas */
        .hero::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: 
                radial-gradient(circle at 20% 30%, rgba(129, 140, 248, 0.15) 0%, transparent 30%),
                radial-gradient(circle at 80% 70%, rgba(192, 132, 252, 0.15) 0%, transparent 35%),
                radial-gradient(circle at 40% 80%, rgba(244, 114, 182, 0.1) 0%, transparent 40%);
            pointer-events: none;
        }
        
        /* Linhas diagonais de fundo */
        .hero::after {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background-image: 
                repeating-linear-gradient(
                    45deg,
                    transparent,
                    transparent 20px,
                    rgba(129, 140, 248, 0.03) 20px,
                    rgba(129, 140, 248, 0.03) 40px
                );
            pointer-events: none;
        }
        
        .hero-content {
            max-width: 1200px;
            margin: 0 auto;
            position: relative;
            z-index: 2;
            display: flex;
            flex-direction: column;
            align-items: center;
            text-align: center;
        }
        
        /* Badge de destaque */
        .hero-badge {
            display: inline-flex;
            align-items: center;
            gap: 10px;
            background: rgba(129, 140, 248, 0.1);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(129, 140, 248, 0.3);
            border-radius: 60px;
            padding: 8px 20px 8px 12px;
            margin-bottom: 40px;
            box-shadow: 0 4px 20px rgba(129, 140, 248, 0.15);
            animation: fadeInDown 0.8s ease-out;
        }
        
        .hero-badge-dot {
            width: 10px;
            height: 10px;
            background: #34d399;
            border-radius: 50%;
            box-shadow: 0 0 20px #34d399;
            animation: pulse 2s infinite;
        }
        
        @keyframes pulse {
            0% { opacity: 1; transform: scale(1); }
            50% { opacity: 0.8; transform: scale(1.1); }
            100% { opacity: 1; transform: scale(1); }
        }
        
        .hero-badge-text {
            color: #cbd5e1;
            font-size: 0.95em;
            font-weight: 500;
            letter-spacing: 0.5px;
        }
        
        .hero-badge-highlight {
            color: #818cf8;
            font-weight: 700;
            margin-left: 4px;
        }
        
        /* Título Principal */
        .hero-title {
            margin-bottom: 30px;
            animation: fadeInUp 0.8s ease-out 0.2s both;
        }
        
        .hero-title-main {
            font-size: 4.5em;
            font-weight: 800;
            letter-spacing: -0.03em;
            line-height: 1.1;
            margin-bottom: 16px;
        }
        
        .gradient-text {
            background: linear-gradient(135deg, #818cf8 0%, #c084fc 50%, #f472b6 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-size: 200% 200%;
            animation: gradient 8s ease infinite;
            display: inline-block;
        }
        
        @keyframes gradient {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }
        
        .hero-title-sub {
            font-size: 2.2em;
            font-weight: 600;
            color: #e2e8f0;
            letter-spacing: -0.02em;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 15px;
            flex-wrap: wrap;
        }
        
        .hero-title-sub-item {
            background: linear-gradient(135deg, #818cf820, #c084fc20);
            padding: 8px 24px;
            border-radius: 60px;
            font-size: 0.7em;
            border: 1px solid rgba(129, 140, 248, 0.3);
            backdrop-filter: blur(10px);
            box-shadow: 0 4px 15px rgba(0,0,0,0.2);
        }
        
        /* Subtítulo */
        .hero-description {
            font-size: 1.3em;
            color: #94a3b8;
            max-width: 800px;
            margin: 0 auto 40px;
            line-height: 1.6;
            animation: fadeInUp 0.8s ease-out 0.4s both;
            position: relative;
            padding: 20px 30px;
            background: rgba(255,255,255,0.02);
            backdrop-filter: blur(10px);
            border-radius: 16px;
            border: 1px solid rgba(129, 140, 248, 0.2);
        }
        
        .hero-description strong {
            color: #818cf8;
            font-weight: 700;
        }
        
        /* Estatísticas rápidas */
        .hero-stats {
            display: flex;
            justify-content: center;
            gap: 60px;
            margin: 40px 0 30px;
            animation: fadeInUp 0.8s ease-out 0.6s both;
        }
        
        .hero-stat-item {
            text-align: center;
        }
        
        .hero-stat-value {
            font-size: 2.2em;
            font-weight: 800;
            background: linear-gradient(135deg, #818cf8, #c084fc);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            line-height: 1.2;
        }
        
        .hero-stat-label {
            color: #64748b;
            font-size: 0.85em;
            text-transform: uppercase;
            letter-spacing: 1px;
            margin-top: 8px;
        }
        
        /* Badges de tecnologia */
        .hero-badges {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 12px;
            margin-top: 20px;
            animation: fadeInUp 0.8s ease-out 0.8s both;
        }
        
        .hero-badge-item {
            padding: 8px 20px;
            background: rgba(255,255,255,0.02);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(129, 140, 248, 0.2);
            border-radius: 40px;
            font-size: 0.9em;
            color: #cbd5e1;
            transition: all 0.3s ease;
        }
        
        .hero-badge-item:hover {
            background: rgba(129, 140, 248, 0.15);
            border-color: #818cf8;
            transform: translateY(-2px);
            box-shadow: 0 8px 20px rgba(129, 140, 248, 0.2);
        }
        
        /* Animações */
        @keyframes fadeInDown {
            from {
                opacity: 0;
                transform: translateY(-20px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }
        
        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(20px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 60px 24px;
        }
        
        .section-title {
            font-size: 2.2em;
            font-weight: 700;
            margin-bottom: 40px;
            position: relative;
            display: inline-block;
            color: #f1f5f9;
        }
        
        .section-title::after {
            content: '';
            position: absolute;
            bottom: -10px;
            left: 0;
            width: 60%;
            height: 4px;
            background: linear-gradient(90deg, #818cf8, #c084fc, #f472b6);
            border-radius: 2px;
        }
        
        .grid-2 {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 32px;
            margin: 40px 0;
        }
        
        .glass-card {
            background: rgba(255,255,255,0.02);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255,255,255,0.05);
            border-radius: 32px;
            padding: 36px;
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
            box-shadow: 0 20px 40px -15px rgba(0,0,0,0.3);
        }
        
        .glass-card:hover {
            border-color: rgba(129, 140, 248, 0.3);
            transform: translateY(-4px);
            box-shadow: 0 30px 60px -15px rgba(129, 140, 248, 0.3);
        }
        
        .card-problem {
            background: linear-gradient(145deg, rgba(239, 68, 68, 0.1) 0%, rgba(185, 28, 28, 0.05) 100%);
        }
        
        .card-solution {
            background: linear-gradient(145deg, rgba(16, 185, 129, 0.1) 0%, rgba(6, 95, 70, 0.05) 100%);
        }
        
        .card-icon {
            font-size: 3em;
            margin-bottom: 24px;
        }
        
        .card h3 {
            font-size: 1.8em;
            margin-bottom: 24px;
            font-weight: 700;
        }
        
        .card-problem h3 { color: #f87171; }
        .card-solution h3 { color: #34d399; }
        
        .list-modern {
            list-style: none;
            padding: 0;
        }
        
        .list-modern li {
            margin-bottom: 18px;
            display: flex;
            align-items: flex-start;
            gap: 12px;
            color: #cbd5e1;
        }
        
        .list-icon {
            width: 24px;
            height: 24px;
            background: rgba(255,255,255,0.05);
            border-radius: 50%;
            display: inline-flex;
            align-items: center;
            justify-content: center;
            font-size: 14px;
            flex-shrink: 0;
            margin-top: 3px;
        }
        
        .result-container {
            margin: 60px 0;
            position: relative;
        }
        
        .result-card {
            background: linear-gradient(145deg, #1e1a3a 0%, #2d1b4e 100%);
            border-radius: 40px;
            padding: 48px;
            position: relative;
            overflow: hidden;
            border: 1px solid rgba(129, 140, 248, 0.2);
        }
        
        .result-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 2px;
            background: linear-gradient(90deg, #818cf8, #c084fc, #f472b6);
        }
        
        .result-tag {
            display: inline-block;
            padding: 8px 20px;
            background: rgba(129, 140, 248, 0.2);
            border-radius: 40px;
            font-size: 0.9em;
            color: #818cf8;
            margin-bottom: 24px;
            border: 1px solid rgba(129, 140, 248, 0.4);
        }
        
        .result-card h2 {
            font-size: 2.5em;
            margin-bottom: 24px;
            color: #f1f5f9;
        }
        
        .result-stats {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 32px;
            margin: 48px 0;
        }
        
        .stat-item {
            text-align: center;
        }
        
        .stat-value {
            font-size: 3.5em;
            font-weight: 800;
            background: linear-gradient(135deg, #818cf8, #c084fc);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            line-height: 1.2;
        }
        
        .stat-label {
            color: #94a3b8;
            font-size: 0.95em;
            text-transform: uppercase;
            letter-spacing: 1px;
        }
        
        .stat-desc {
            color: #64748b;
            font-size: 0.85em;
            margin-top: 8px;
        }
        
        .structure-container {
            background: #0f0f1a;
            border-radius: 24px;
            padding: 32px;
            border: 1px solid rgba(255,255,255,0.05);
            font-family: 'Fira Code', 'JetBrains Mono', monospace;
            margin: 40px 0;
        }
        
        .structure-header {
            display: flex;
            align-items: center;
            gap: 12px;
            margin-bottom: 24px;
            padding-bottom: 16px;
            border-bottom: 1px solid rgba(255,255,255,0.1);
        }
        
        .structure-dot {
            width: 12px;
            height: 12px;
            border-radius: 50%;
            background: #f87171;
            box-shadow: 0 0 10px #f87171;
        }
        
        .structure-dot:nth-child(2) { background: #fbbf24; box-shadow: 0 0 10px #fbbf24; }
        .structure-dot:nth-child(3) { background: #34d399; box-shadow: 0 0 10px #34d399; }
        
        .folder { color: #818cf8; font-weight: 600; }
        .file { color: #94a3b8; margin-left: 24px; }
        .comment { color: #64748b; font-style: italic; }
        
        .features-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 24px;
            margin: 40px 0;
        }
        
        .feature-block {
            background: rgba(255,255,255,0.02);
            border-radius: 24px;
            padding: 28px;
            border: 1px solid rgba(255,255,255,0.05);
            transition: all 0.3s ease;
        }
        
        .feature-block:hover {
            border-color: #818cf8;
            transform: translateY(-4px);
        }
        
        .feature-icon-large {
            font-size: 2.5em;
            margin-bottom: 20px;
        }
        
        .feature-title {
            font-size: 1.3em;
            font-weight: 600;
            margin-bottom: 12px;
            color: #f1f5f9;
        }
        
        .feature-desc {
            color: #94a3b8;
            font-size: 0.95em;
            line-height: 1.6;
        }
        
        .timeline-modern {
            margin: 40px 0;
        }
        
        .timeline-step {
            display: flex;
            gap: 24px;
            margin-bottom: 24px;
            position: relative;
        }
        
        .timeline-step:not(:last-child)::before {
            content: '';
            position: absolute;
            left: 20px;
            top: 50px;
            bottom: -24px;
            width: 2px;
            background: linear-gradient(180deg, #818cf8, transparent);
        }
        
        .step-number {
            width: 44px;
            height: 44px;
            background: linear-gradient(135deg, #818cf8, #c084fc);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 700;
            font-size: 1.2em;
            color: #0b0f1a;
            flex-shrink: 0;
            position: relative;
            z-index: 2;
            box-shadow: 0 0 20px #818cf8;
        }
        
        .step-content {
            flex: 1;
            background: rgba(255,255,255,0.02);
            border-radius: 20px;
            padding: 24px;
            border: 1px solid rgba(255,255,255,0.05);
        }
        
        .step-title {
            font-size: 1.3em;
            font-weight: 600;
            color: #f1f5f9;
            margin-bottom: 8px;
        }
        
        .tech-pills {
            display: flex;
            flex-wrap: wrap;
            gap: 12px;
            margin: 32px 0;
        }
        
        .tech-pill {
            padding: 12px 28px;
            background: linear-gradient(145deg, rgba(129, 140, 248, 0.1) 0%, rgba(192, 132, 252, 0.1) 100%);
            border: 1px solid rgba(129, 140, 248, 0.3);
            border-radius: 40px;
            font-weight: 500;
            color: #e2e8f0;
            transition: all 0.3s ease;
            backdrop-filter: blur(4px);
        }
        
        .tech-pill:hover {
            background: rgba(129, 140, 248, 0.2);
            border-color: #818cf8;
            transform: scale(1.05);
        }
        
        .execution-box {
            background: #0f0f1a;
            border-radius: 28px;
            padding: 36px;
            border: 1px solid #818cf8;
            margin: 40px 0;
            position: relative;
            overflow: hidden;
        }
        
        .execution-box::before {
            content: '>';
            position: absolute;
            bottom: 20px;
            right: 30px;
            font-size: 8em;
            color: rgba(129, 140, 248, 0.05);
            font-weight: 800;
        }
        
        .command-line {
            background: #1a1a2a;
            border-radius: 16px;
            padding: 16px 24px;
            font-family: 'Fira Code', monospace;
            color: #34d399;
            margin: 16px 0;
            border: 1px solid rgba(255,255,255,0.1);
            position: relative;
            overflow-x: auto;
        }
        
        .command-line::before {
            content: '$';
            color: #818cf8;
            margin-right: 12px;
        }
        
        .footer {
            text-align: center;
            padding: 60px 24px 40px;
            border-top: 1px solid rgba(255,255,255,0.05);
            margin-top: 60px;
        }
        
        .footer-gradient {
            font-size: 2em;
            font-weight: 700;
            background: linear-gradient(135deg, #818cf8, #c084fc);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            margin-bottom: 16px;
        }
        
        @media (max-width: 768px) {
            .hero-title-main { font-size: 2.8em; }
            .hero-title-sub { font-size: 1.5em; }
            .hero-stats { flex-direction: column; gap: 20px; }
            .grid-2 { grid-template-columns: 1fr; }
            .features-grid { grid-template-columns: 1fr; }
            .result-stats { grid-template-columns: 1fr; }
            .result-card { padding: 28px; }
        }
    </style>
</head>
<body>
    <!-- Hero Section Aprimorada -->
    <section class="hero">
        <div class="hero-content">
            <!-- Badge animado -->
            <div 
            </div>
            
            <!-- Título Principal com novo texto -->
            <div class="hero-title">
                <h1 class="hero-title-main">
                    <span class="gradient-text">Pipeline de Dados</span>
                </h1>
                <div class="hero-title-sub">
                    <span class="hero-title-sub-item">ETL</span>
                    <span>•</span>
                    <span class="hero-title-sub-item">Vendas</span>
                    <span>•</span>
                    <span class="hero-title-sub-item">Gestão Comercial</span>
                </div>
            </div>
            
            <!-- Descrição impactante -->
            <div class="hero-description">
                Transformação de dados de vendas em <strong>informação estratégica</strong>.<br>
            </div>
            
            <!-- Estatísticas rápidas -->
            <div class="hero-stats">
                <div class="hero-stat-item">
                    <div class="hero-stat-value">100%</div>
                    <div class="hero-stat-label">Qualidade</div>
                </div>
                <div class="hero-stat-item">
                    <div class="hero-stat-value">0</div>
                    <div class="hero-stat-label">Duplicatas</div>
                </div>
                <div class="hero-stat-item">
                    <div class="hero-stat-value">∞</div>
                    <div class="hero-stat-label">Escalabilidade</div>
                </div>
            </div>
            
            <!-- Badges de tecnologia -->
            <div class="hero-badges">
                <span class="hero-badge-item">🐍 Python 3.14</span>
                <span class="hero-badge-item">📊 Pandas 2.3.3</span>
                <span class="hero-badge-item">🗄️ SQLite 3</span>
                <span class="hero-badge-item">📈 OpenPyXL</span>
               </div>
        </div>
    </section>

    <div class="container">
        <!-- Problema vs Solução -->
        <div class="grid-2">
            <div class="glass-card card-problem">
                <div class="card-icon">⚠️ Desafio</div>
                <h3></h3>
                <ul class="list-modern">
                    <li><span class="list-icon">🔴</span> Dados fragmentados em formatos distintos (CSV e Excel)</li>
                    <li><span class="list-icon">🔴</span> Inconsistências críticas: valores nulos sem tratamento</li>
                    <li><span class="list-icon">🔴</span> Datas com formatação incorreta e horários desnecessários</li>
                    <li><span class="list-icon">🔴</span> Registros duplicados comprometendo análises</li>
                    <li><span class="list-icon">🔴</span> Ausência de integridade relacional entre bases</li>
                </ul>
            </div>
            
            <div class="glass-card card-solution">
                <div class="card-icon">✅ Solução</div>
                <h3></h3>
                <ul class="list-modern">
                    <li><span class="list-icon">🟢</span> Extração automatizada de múltiplas fontes</li>
                    <li><span class="list-icon">🟢</span> Pipeline de transformação com Pandas</li>
                    <li><span class="list-icon">🟢</span> Padronização de formatos e remoção de horários</li>
                    <li><span class="list-icon">🟢</span> Tratamento inteligente de nulos e duplicatas</li>
                    <li><span class="list-icon">🟢</span> Modelo relacional com chaves estrangeiras</li>
                </ul>
            </div>
        </div>

        <!-- Resultado em Destaque -->
        <div class="result-container">
            <div class="result-card">
                <span class="result-tag">📊 Resultado</span>
                <h2>Dados Consistentes • Análises Confiáveis</h2>
                <p style="color: #cbd5e1; font-size: 1.2em; max-width: 800px;">
                    Base única e estruturada, pronta para consumo em qualquer banco relacional (SQLite, PostgreSQL, MySQL). 
                    Dados íntegros para informações precisas sobre performance de vendas por gerente, região e produto.
                </p>
                
                <div class="result-stats">
                    <div class="stat-item">
                        <div class="stat-value">100%</div>
                        <div class="stat-label">Qualidade</div>
                        <div class="stat-desc">Dados consistentes</div>
                    </div>
                    <div class="stat-item">
                        <div class="stat-value">0</div>
                        <div class="stat-label">Duplicatas</div>
                        <div class="stat-desc">Registros únicos garantidos</div>
                    </div>
                    <div class="stat-item">
                        <div class="stat-value">∞</div>
                        <div class="stat-label">Escalável</div>
                        <div class="stat-desc">Qualquer volume de dados</div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Estrutura do Projeto -->
        <h2 class="section-title">📁 Estrutura do Projeto</h2>
        <div class="structure-container">
            <div class="structure-header">
                <span class="structure-dot"></span>
                <span class="structure-dot"></span>
                <span class="structure-dot"></span>
            </div>
            <div><span class="folder">📦 pipeline-dados/</span> <span class="comment"># Raiz do projeto</span></div>
            <div class="file">├── <span style="color: #fff;">ETL.py</span> <span class="comment"># Orquestrador principal</span></div>
            <div class="file">├── <span style="color: #fff;">comp.py</span> <span class="comment"># Extração + Transformação</span></div>
            <div class="file">├── <span style="color: #fff;">database.py</span> <span class="comment"># Conexão SQLite + Carga</span></div>
            <div class="file">├── <span style="color: #fff;">vendas.db</span> <span class="comment"># Banco gerado automaticamente</span></div>
            <div class="file">├── <span style="color: #fff;">requirements.txt</span> <span class="comment"># Dependências</span></div>
            <div class="file">└── <span class="folder">dados/</span> <span class="comment"># Diretório de entrada</span></div>
            <div class="file" style="margin-left: 48px;">├── vendas.csv <span class="comment"># Dados brutos de vendas</span></div>
            <div class="file" style="margin-left: 48px;">└── gerentes.xlsx <span class="comment"># Dados brutos de gerentes</span></div>
        </div>

        <!-- Funcionalidades Detalhadas -->
        <h2 class="section-title">⚡ Funcionalidades</h2>
        <div class="features-grid">
            <div class="feature-block">
                <div class="feature-icon-large">🧹</div>
                <div class="feature-title">Data Cleaning</div>
                <div class="feature-desc">Remoção automática de colunas irrelevantes e tratamento inteligente de valores nulos com fallback "Online"</div>
            </div>
            <div class="feature-block">
                <div class="feature-icon-large">📅</div>
                <div class="feature-title">Date Normalization</div>
                <div class="feature-desc">Conversão e padronização de datas no formato ISO (YYYY-MM-DD) com remoção de timestamps</div>
            </div>
            <div class="feature-block">
                <div class="feature-icon-large">🆔</div>
                <div class="feature-title">Deduplication</div>
                <div class="feature-desc">Identificação e remoção de registros duplicados baseada em chaves únicas (ID)</div>
            </div>
            <div class="feature-block">
                <div class="feature-icon-large">🔗</div>
                <div class="feature-title">Relational Integrity</div>
                <div class="feature-desc">Modelo de dados com chaves estrangeiras garantindo consistência referencial</div>
            </div>
            <div class="feature-block">
                <div class="feature-icon-large">🏪</div>
                <div class="feature-title">Smart Fill</div>
                <div class="feature-desc">Preenchimento automático de lojas não identificadas com "Online"</div>
            </div>
            <div class="feature-block">
                <div class="feature-icon-large">📊</div>
                <div class="feature-title">Derived Metrics</div>
                <div class="feature-desc">Cálculo automático de valor total das vendas (quantidade × preço unitário)</div>
            </div>
        </div>

        <!-- Fluxo do Pipeline -->
        <h2 class="section-title">🔄 Pipeline Flow</h2>
        <div class="timeline-modern">
            <div class="timeline-step">
                <div class="step-number">1</div>
                <div class="step-content">
                    <div class="step-title">Extração</div>
                    <p style="color: #94a3b8;">Leitura otimizada dos arquivos fonte com Pandas: vendas.csv e gerentes.xlsx, com tratamento de encoding e baixo consumo de memória</p>
                </div>
            </div>
            <div class="timeline-step">
                <div class="step-number">2</div>
                <div class="step-content">
                    <div class="step-title">Transformação</div>
                    <p style="color: #94a3b8;">Aplicação das regras de negócio: remoção de DATA_BASE, preenchimento de LOJA, drop de nulos, padronização de datas e deduplicação</p>
                </div>
            </div>
            <div class="timeline-step">
                <div class="step-number">3</div>
                <div class="step-content">
                    <div class="step-title">Modelagem</div>
                    <p style="color: #94a3b8;">Criação automática das tabelas gerentes e vendas com relacionamento por chave estrangeira e constraints de integridade</p>
                </div>
            </div>
            <div class="timeline-step">
                <div class="step-number">4</div>
                <div class="step-content">
                    <div class="step-title">Carga</div>
                    <p style="color: #94a3b8;">Inserção dos dados processados no SQLite com validação de tipos e integridade referencial</p>
                </div>
            </div>
        </div>

        <!-- Stack Tecnológica -->
        <h2 class="section-title">🛠️ Tech Stack</h2>
        <div class="tech-pills">
            <span class="tech-pill">Python 3.14</span>
            <span class="tech-pill">Pandas 2.3.3</span>
            <span class="tech-pill">SQLite3</span>
            <span class="tech-pill">OpenPyXL</span>
            <span class="tech-pill">NumPy</span>
            <span class="tech-pill">PathLib</span>
            <span class="tech-pill">SQL</span>
            <span class="tech-pill">ETL Architecture</span>
        </div>

        <!-- Execução -->
        <h2 class="section-title">🚀 Quick Start</h2>
        <div class="execution-box">
            <p style="color: #818cf8; margin-bottom: 24px; font-weight: 600;">⚡ Execute em 4 passos:</p>
            <div class="command-line">git clone https://github.com/seu-repo/pipeline-dados</div>
            <div class="command-line">pip install pandas openpyxl</div>
            <div class="command-line"># Adicione seus arquivos em /dados</div>
            <div class="command-line">python ETL.py</div>
            <p style="color: #34d399; margin-top: 24px;">✅ Banco vendas.db gerado automaticamente com dados consistentes</p>
        </div>

        <!-- Pré-requisitos -->
        <h2 class="section-title">📋 Pré-requisitos</h2>
        <div style="background: rgba(255,255,255,0.02); border-radius: 24px; padding: 32px; margin: 
