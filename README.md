# Cardapio-html---Pokemon
html5
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title></title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Press+Start+2P&family=Roboto:wght@400;700&display=swap');
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Roboto', sans-serif;
            background: linear-gradient(135deg, #1a1a2e 0%, #16213e 50%, #0f3460 100%);
            min-height: 100vh;
            padding: 20px;
            color: #fff;
        }
        
        .container {
            max-width: 800px;
            margin: 0 auto;
            background: rgba(255, 255, 255, 0.05);
            border-radius: 20px;
            padding: 40px;
            backdrop-filter: blur(10px);
            border: 2px solid rgba(255, 255, 255, 0.1);
            box-shadow: 0 20px 60px rgba(0, 0, 0, 0.5);
        }
        
        header {
            text-align: center;
            margin-bottom: 40px;
            position: relative;
        }
        
        .pokeball {
            width: 80px;
            height: 80px;
            margin: 0 auto 20px;
            background: linear-gradient(to bottom, #ff0000 0%, #ff0000 48%, #000 48%, #000 52%, #fff 52%, #fff 100%);
            border-radius: 50%;
            border: 4px solid #000;
            position: relative;
            animation: float 3s ease-in-out infinite;
            box-shadow: 0 10px 30px rgba(255, 0, 0, 0.3);
        }
        
        .pokeball::before {
            content: '';
            position: absolute;
            width: 24px;
            height: 24px;
            background: #fff;
            border: 4px solid #000;
            border-radius: 50%;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
        }
        
        @keyframes float {
            0%, 100% { transform: translateY(0px); }
            50% { transform: translateY(-10px); }
        }
        
        h1 {
            font-family: 'Press Start 2P', cursive;
            font-size: 2.5em;
            color: #ffcb05;
            text-shadow: 4px 4px 0px #3c5aa6;
            margin-bottom: 10px;
            letter-spacing: 2px;
        }
        
        .subtitle {
            font-size: 1.2em;
            color: #3c5aa6;
            font-weight: bold;
            text-transform: uppercase;
            letter-spacing: 3px;
        }
        
        .menu-grid {
            display: grid;
            gap: 25px;
        }
        
        .drink-card {
            background: linear-gradient(145deg, rgba(255,255,255,0.1) 0%, rgba(255,255,255,0.05) 100%);
            border-radius: 15px;
            padding: 25px;
            display: flex;
            align-items: center;
            gap: 20px;
            border: 2px solid rgba(255, 255, 255, 0.1);
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }
        
        .drink-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.1), transparent);
            transition: left 0.5s;
        }
        
        .drink-card:hover::before {
            left: 100%;
        }
        
        .drink-card:hover {
            transform: translateX(10px);
            border-color: rgba(255, 203, 5, 0.5);
            box-shadow: 0 10px 30px rgba(255, 203, 5, 0.2);
        }
        
        .pokemon-img {
            width: 100px;
            height: 100px;
            object-fit: contain;
            filter: drop-shadow(0 5px 15px rgba(0,0,0,0.3));
            transition: transform 0.3s ease;
        }
        
        .drink-card:hover .pokemon-img {
            transform: scale(1.1) rotate(5deg);
        }
        
        .drink-info {
            flex: 1;
        }
        
        .drink-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 8px;
            flex-wrap: wrap;
            gap: 10px;
        }
        
        .drink-name {
            font-family: 'Press Start 2P', cursive;
            font-size: 1.1em;
            color: #ffcb05;
            text-shadow: 2px 2px 0px #000;
        }
        
        .price {
            background: #ff0000;
            color: white;
            padding: 5px 15px;
            border-radius: 20px;
            font-weight: bold;
            font-size: 1.2em;
            box-shadow: 0 4px 10px rgba(255, 0, 0, 0.3);
            border: 2px solid #000;
        }
        
        .drink-type {
            display: inline-block;
            background: rgba(255, 255, 255, 0.1);
            padding: 3px 10px;
            border-radius: 10px;
            font-size: 0.8em;
            margin-bottom: 8px;
            color: #ffcb05;
            font-weight: bold;
        }
        
        .description {
            color: #120e0e;
            line-height: 1.6;
            font-size: 0.95em;
        }
        
        .type-rock { border-left: 4px solid #a8a878; }
        .type-steel { border-left: 4px solid #b8b8d0; }
        .type-grass { border-left: 4px solid #78c850; }
        .type-electric { border-left: 4px solid #f8d030; }
        .type-fire { border-left: 4px solid #f08030; }
        
        /* ===== BADGE DE EVOLUÇÃO ===== */
        .evolution-badge {
            position: absolute;
            top: -12px;
            right: -12px;
            font-family: 'Press Start 2P', cursive;
            font-size: 0.55em;
            padding: 8px 12px;
            border-radius: 20px;
            border: 2px solid #000;
            animation: pulse-badge 2s infinite;
            z-index: 10;
            box-shadow: 0 4px 15px rgba(0,0,0,0.3);
        }
        
        /* Cores específicas por tipo */
        .type-steel .evolution-badge {
            background: linear-gradient(135deg, #b8b8d0, #7a7a94);
            color: #1a1a2e;
            box-shadow: 0 4px 15px rgba(184, 184, 208, 0.5);
        }
        
        .type-fire .evolution-badge {
            background: linear-gradient(135deg, #ff4500, #ff8c00);
            color: white;
            box-shadow: 0 4px 15px rgba(255, 69, 0, 0.5);
        }
        
        @keyframes pulse-badge {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.05); }
        }
        
        /* ===== STEELIX - EVOLUÇÃO ESPECIAL ===== */
        .drink-card.type-steel.steelix {
            background: linear-gradient(145deg, 
                rgba(184, 184, 208, 0.15) 0%, 
                rgba(122, 122, 148, 0.1) 50%, 
                rgba(184, 184, 208, 0.15) 100%
            );
            border: 2px solid transparent;
            position: relative;
            overflow: visible;
            transform: scale(1.02);
        }
        
        /* Borda metálica animada */
        .steelix::after {
            content: '';
            position: absolute;
            inset: -3px;
            border-radius: 17px;
            padding: 3px;
            background: linear-gradient(45deg, #b8b8d0, #7a7a94, #d1d1e0, #b8b8d0);
            background-size: 400% 400%;
            animation: steel-shine 3s ease infinite;
            -webkit-mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0);
            mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0);
            -webkit-mask-composite: xor;
            mask-composite: exclude;
            z-index: -1;
        }
        
        @keyframes steel-shine {
            0%, 100% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
        }
        
        /* Efeito de metal no hover */
        .steelix:hover {
            transform: translateX(10px) scale(1.03);
            box-shadow: 0 15px 40px rgba(184, 184, 208, 0.4), 0 0 60px rgba(122, 122, 148, 0.2);
        }
        
        /* Ícone de metal no título */
        .drink-name.steelix-name::before {
            content: '⛓️ ';
        }
        
        /* Onix mais "básico" para contraste */
        .drink-card.type-rock:not(.steelix) {
            opacity: 0.95;
        }
        
        /* ===== CHARIZARD - EVOLUÇÃO ESPECIAL ===== */
        @keyframes flame-border {
            0%, 100% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
        }
        
        @keyframes flicker {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.8; }
        }
        
        @keyframes ember-float {
            0% { transform: translateY(0) scale(1); opacity: 1; }
            100% { transform: translateY(-30px) scale(0.5); opacity: 0; }
        }
        
        /* Card especial Charizard */
        .drink-card.type-fire.charizard {
            background: linear-gradient(145deg, 
                rgba(255,69,0,0.15) 0%, 
                rgba(255,140,0,0.1) 50%, 
                rgba(255,69,0,0.15) 100%
            );
            border: 2px solid transparent;
            position: relative;
            overflow: visible;
            transform: scale(1.02);
            margin-top: 10px;
        }
        
        /* Borda flamejante animada */
        .charizard::after {
            content: '';
            position: absolute;
            inset: -3px;
            border-radius: 17px;
            padding: 3px;
            background: linear-gradient(45deg, #ff4500, #ff8c00, #ff4500, #dc143c);
            background-size: 400% 400%;
            animation: flame-border 3s ease infinite;
            -webkit-mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0);
            mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0);
            -webkit-mask-composite: xor;
            mask-composite: exclude;
            z-index: -1;
        }
        
        /* Ícone de fogo no título */
        .drink-name.charizard-name::before {
            content: '🔥 ';
            animation: flicker 1.5s infinite;
        }
        
        /* Indicador de pimenta */
        .spice-level::after {
            content: '🌶️';
            filter: drop-shadow(0 0 5px #ff4500);
            font-size: 1.2em;
        }
        
        /* Brasas */
        .ember {
            position: absolute;
            width: 8px;
            height: 8px;
            background: radial-gradient(circle, #ff8c00 0%, #ff4500 50%, transparent 100%);
            border-radius: 50%;
            pointer-events: none;
            opacity: 0;
        }
        
        .charizard:hover .ember {
            animation: ember-float 1s ease-out infinite;
        }
        
        /* Efeito de calor no hover */
        .charizard:hover {
            transform: translateX(10px) scale(1.03);
            box-shadow: 0 15px 40px rgba(255,69,0,0.4), 0 0 60px rgba(255,140,0,0.2);
        }
        
        /* Charmander mais "básico" para contraste */
        .drink-card.type-fire:not(.charizard) {
            opacity: 0.95;
        }
        
        footer {
            text-align: center;
            margin-top: 40px;
            padding-top: 20px;
            border-top: 2px solid rgba(255, 255, 255, 0.1);
            color: #888;
            font-size: 0.9em;
        }
        
        .trainer-tip {
            background: rgba(255, 203, 5, 0.1);
            border: 2px dashed #ffcb05;
            border-radius: 10px;
            padding: 15px;
            margin-top: 20px;
            text-align: center;
            font-style: italic;
            color: #ffcb05;
        }
        
        @media print {
            body {
                background: #1a1a2e;
                -webkit-print-color-adjust: exact;
                print-color-adjust: exact;
            }
            .container {
                box-shadow: none;
                border: 2px solid #333;
            }
            .drink-card {
                break-inside: avoid;
                page-break-inside: avoid;
            }
        }
        
        @media (max-width: 600px) {
            h1 { font-size: 1.8em; }
            .drink-card { flex-direction: column; text-align: center; }
            .drink-header { justify-content: center; }
            .evolution-badge { 
                top: -8px; 
                right: 50%; 
                transform: translateX(50%);
                font-size: 0.5em;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <div class="pokeball"></div>
           
            <p class="subtitle">Cardápio de Drinks Especiais</p>
        </header>
        
        <div class="menu-grid">
            <!-- Onix - Espresso Martini (BÁSICO) -->
            <div class="drink-card type-rock">
                <img src="https://kimi-web-img.moonshot.cn/img/img.pokemondb.net/2c25ba13688420ab32227c6fedd1951c99ccb55d.png" alt="Onix" class="pokemon-img">
                <div class="drink-info">
                    <div class="drink-header">
                        <span class="drink-type">Tipo Pedra</span>
                        <span class="price">R$ 27</span>
                    </div>
                    <div class="drink-header">
                        <h2 class="drink-name">ONIX</h2>
                    </div>
                    <p class="description">
                        <strong>Espresso Martini</strong><br>
                        Café expresso batido com vodka e licor de café, finalizado com grãos de café. 
                        Forte como o corpo de rocha do Onix!
                    </p>
                </div>
            </div>
            
            <!-- ⛓️ STEELIX - EVOLUÇÃO ⛓️ -->
            <div class="drink-card type-steel steelix">
                <span class="evolution-badge">EVOLUÇÃO!</span>
                
                <img src="https://kimi-web-img.moonshot.cn/img/img.pokemondb.net/04de07080987c4f26571cfe886ab8c149e91a436.png" alt="Steelix" class="pokemon-img">
                
                <div class="drink-info">
                    <div class="drink-header">
                        <span class="drink-type">Tipo Aço ⛓️</span>
                        <span class="price">R$ 30</span>
                    </div>
                    <div class="drink-header">
                        <h2 class="drink-name steelix-name">STEELIX</h2>
                    </div>
                    <p class="description">
                        <strong>Espresso Martini Premium</strong><br>
                        A evolução do Onix! Espresso martini com adição de licor de chocolate meio amargo 
                        e raspas de ouro comestível. <strong>Robusto, sofisticado e inquebrável</strong> como aço!
                    </p>
                </div>
            </div>
            
            <!-- Bulbasaur - Caipirosca de Limão -->
            <div class="drink-card type-grass">
                <img src="https://kimi-web-img.moonshot.cn/img/img.pokemondb.net/748d7aa83dc70756c96ba01b50735994e55d0c27.jpg" alt="Bulbasaur" class="pokemon-img">
                <div class="drink-info">
                    <div class="drink-header">
                        <span class="drink-type">Tipo Grama</span>
                        <span class="price">R$ 20</span>
                    </div>
                    <div class="drink-header">
                        <h2 class="drink-name">BULBASSAURO</h2>
                    </div>
                    <p class="description">
                        <strong>Caipirosca de Limão</strong><br>
                        Vodka, limão fresco, açúcar e gelo. Refrescante como o aroma das flores do bulbo nas costas deste Pokémon.
                    </p>
                </div>
            </div>
            
            <!-- Pikachu - Brasileirinha -->
            <div class="drink-card type-electric">
                <img src="https://kimi-web-img.moonshot.cn/img/img.pokemondb.net/3f7f50afeb428883569447e84157e88b22281470.jpg" alt="Pikachu" class="pokemon-img">
                <div class="drink-info">
                    <div class="drink-header">
                        <span class="drink-type">Tipo Elétrico</span>
                        <span class="price">R$ 25</span>
                    </div>
                    <div class="drink-header">
                        <h2 class="drink-name">PIKACHU</h2>
                    </div>
                    <p class="description">
                        <strong>Brasileirinha</strong><br>
                        Maracujá, limão, açúcar, gelo e vodka. Um choque de sabor tropical! 
                        Eletrificante como um Thunderbolt.
                    </p>
                </div>
            </div>
            
            <!-- Charmander - Caipirosca de Morango (BÁSICO) -->
            <div class="drink-card type-fire">
                <img src="https://kimi-web-img.moonshot.cn/img/img.pokemondb.net/2ae27be9adfd55f331dccda361f5eca87c3f9724.jpg" alt="Charmander" class="pokemon-img">
                <div class="drink-info">
                    <div class="drink-header">
                        <span class="drink-type">Tipo Fogo</span>
                        <span class="price">R$ 23</span>
                    </div>
                    <div class="drink-header">
                        <h2 class="drink-name">CHARMANDER</h2>
                    </div>
                    <p class="description">
                        <strong>Caipirosca de Morango</strong><br>
                        Vodka, morangos frescos, açúcar e gelo.
                        
                    </p>
                </div>
            </div>
            
            <!-- 🔥 CHARIZARD - EVOLUÇÃO 🔥 -->
            <div class="drink-card type-fire charizard">
                <span class="evolution-badge">EVOLUÇÃO!</span>
                <div class="ember" style="left: 20%; top: 80%;"></div>
                <div class="ember" style="left: 50%; top: 85%; animation-delay: 0.3s;"></div>
                <div class="ember" style="left: 80%; top: 80%; animation-delay: 0.6s;"></div>
                
                <img src="https://img.pokemondb.net/artwork/large/charizard.jpg" alt="Charizard" class="pokemon-img">
                
                <div class="drink-info">
                    <div class="drink-header">
                        <span class="drink-type">Tipo Fogo 🔥</span>
                        <span class="price">R$ 25</span>
                    </div>
                    <div class="drink-header">
                        <h2 class="drink-name charizard-name">CHARIZARD</h2>
                        <span class="spice-level" title="Nível de pimenta: Médio"></span>
                    </div>
                    <p class="description">
                        <strong>Caipirosca de Morango Picante</strong><br>
                        A evolução final! Vodka, morangos frescos, açúcar gelo e um 
                        <em>toque de pimenta</em> que incendia o paladar. 
                        Assim como a chama de Charizard, esse drink é <strong>intenso e inesquecível</strong>!
                    </p>
                </div>
            </div>
        </div>
        
        <div class="trainer-tip">
            💡 Dica do Treinador: Evolua seus drinks! Onix → Steelix | Charmander → Charizard
        </div>
        
        <footer>
            
        </footer>
    </div>
</body>
</html><!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title></title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Press+Start+2P&family=Roboto:wght@400;700&display=swap');
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Roboto', sans-serif;
            background: linear-gradient(135deg, #1a1a2e 0%, #16213e 50%, #0f3460 100%);
            min-height: 100vh;
            padding: 20px;
            color: #fff;
        }
        
        .container {
            max-width: 800px;
            margin: 0 auto;
            background: rgba(255, 255, 255, 0.05);
            border-radius: 20px;
            padding: 40px;
            backdrop-filter: blur(10px);
            border: 2px solid rgba(255, 255, 255, 0.1);
            box-shadow: 0 20px 60px rgba(0, 0, 0, 0.5);
        }
        
        header {
            text-align: center;
            margin-bottom: 40px;
            position: relative;
        }
        
        .pokeball {
            width: 80px;
            height: 80px;
            margin: 0 auto 20px;
            background: linear-gradient(to bottom, #ff0000 0%, #ff0000 48%, #000 48%, #000 52%, #fff 52%, #fff 100%);
            border-radius: 50%;
            border: 4px solid #000;
            position: relative;
            animation: float 3s ease-in-out infinite;
            box-shadow: 0 10px 30px rgba(255, 0, 0, 0.3);
        }
        
        .pokeball::before {
            content: '';
            position: absolute;
            width: 24px;
            height: 24px;
            background: #fff;
            border: 4px solid #000;
            border-radius: 50%;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
        }
        
        @keyframes float {
            0%, 100% { transform: translateY(0px); }
            50% { transform: translateY(-10px); }
        }
        
        h1 {
            font-family: 'Press Start 2P', cursive;
            font-size: 2.5em;
            color: #ffcb05;
            text-shadow: 4px 4px 0px #3c5aa6;
            margin-bottom: 10px;
            letter-spacing: 2px;
        }
        
        .subtitle {
            font-size: 1.2em;
            color: #3c5aa6;
            font-weight: bold;
            text-transform: uppercase;
            letter-spacing: 3px;
        }
        
        .menu-grid {
            display: grid;
            gap: 25px;
        }
        
        .drink-card {
            background: linear-gradient(145deg, rgba(255,255,255,0.1) 0%, rgba(255,255,255,0.05) 100%);
            border-radius: 15px;
            padding: 25px;
            display: flex;
            align-items: center;
            gap: 20px;
            border: 2px solid rgba(255, 255, 255, 0.1);
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }
        
        .drink-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.1), transparent);
            transition: left 0.5s;
        }
        
        .drink-card:hover::before {
            left: 100%;
        }
        
        .drink-card:hover {
            transform: translateX(10px);
            border-color: rgba(255, 203, 5, 0.5);
            box-shadow: 0 10px 30px rgba(255, 203, 5, 0.2);
        }
        
        .pokemon-img {
            width: 100px;
            height: 100px;
            object-fit: contain;
            filter: drop-shadow(0 5px 15px rgba(0,0,0,0.3));
            transition: transform 0.3s ease;
        }
        
        .drink-card:hover .pokemon-img {
            transform: scale(1.1) rotate(5deg);
        }
        
        .drink-info {
            flex: 1;
        }
        
        .drink-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 8px;
            flex-wrap: wrap;
            gap: 10px;
        }
        
        .drink-name {
            font-family: 'Press Start 2P', cursive;
            font-size: 1.1em;
            color: #ffcb05;
            text-shadow: 2px 2px 0px #000;
        }
        
        .price {
            background: #ff0000;
            color: white;
            padding: 5px 15px;
            border-radius: 20px;
            font-weight: bold;
            font-size: 1.2em;
            box-shadow: 0 4px 10px rgba(255, 0, 0, 0.3);
            border: 2px solid #000;
        }
        
        .drink-type {
            display: inline-block;
            background: rgba(255, 255, 255, 0.1);
            padding: 3px 10px;
            border-radius: 10px;
            font-size: 0.8em;
            margin-bottom: 8px;
            color: #ffcb05;
            font-weight: bold;
        }
        
        .description {
            color: #120e0e;
            line-height: 1.6;
            font-size: 0.95em;
        }
        
        .type-rock { border-left: 4px solid #a8a878; }
        .type-steel { border-left: 4px solid #b8b8d0; }
        .type-grass { border-left: 4px solid #78c850; }
        .type-electric { border-left: 4px solid #f8d030; }
        .type-fire { border-left: 4px solid #f08030; }
        
        /* ===== BADGE DE EVOLUÇÃO ===== */
        .evolution-badge {
            position: absolute;
            top: -12px;
            right: -12px;
            font-family: 'Press Start 2P', cursive;
            font-size: 0.55em;
            padding: 8px 12px;
            border-radius: 20px;
            border: 2px solid #000;
            animation: pulse-badge 2s infinite;
            z-index: 10;
            box-shadow: 0 4px 15px rgba(0,0,0,0.3);
        }
        
        /* Cores específicas por tipo */
        .type-steel .evolution-badge {
            background: linear-gradient(135deg, #b8b8d0, #7a7a94);
            color: #1a1a2e;
            box-shadow: 0 4px 15px rgba(184, 184, 208, 0.5);
        }
        
        .type-fire .evolution-badge {
            background: linear-gradient(135deg, #ff4500, #ff8c00);
            color: white;
            box-shadow: 0 4px 15px rgba(255, 69, 0, 0.5);
        }
        
        @keyframes pulse-badge {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.05); }
        }
        
        /* ===== STEELIX - EVOLUÇÃO ESPECIAL ===== */
        .drink-card.type-steel.steelix {
            background: linear-gradient(145deg, 
                rgba(184, 184, 208, 0.15) 0%, 
                rgba(122, 122, 148, 0.1) 50%, 
                rgba(184, 184, 208, 0.15) 100%
            );
            border: 2px solid transparent;
            position: relative;
            overflow: visible;
            transform: scale(1.02);
        }
        
        /* Borda metálica animada */
        .steelix::after {
            content: '';
            position: absolute;
            inset: -3px;
            border-radius: 17px;
            padding: 3px;
            background: linear-gradient(45deg, #b8b8d0, #7a7a94, #d1d1e0, #b8b8d0);
            background-size: 400% 400%;
            animation: steel-shine 3s ease infinite;
            -webkit-mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0);
            mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0);
            -webkit-mask-composite: xor;
            mask-composite: exclude;
            z-index: -1;
        }
        
        @keyframes steel-shine {
            0%, 100% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
        }
        
        /* Efeito de metal no hover */
        .steelix:hover {
            transform: translateX(10px) scale(1.03);
            box-shadow: 0 15px 40px rgba(184, 184, 208, 0.4), 0 0 60px rgba(122, 122, 148, 0.2);
        }
        
        /* Ícone de metal no título */
        .drink-name.steelix-name::before {
            content: '⛓️ ';
        }
        
        /* Onix mais "básico" para contraste */
        .drink-card.type-rock:not(.steelix) {
            opacity: 0.95;
        }
        
        /* ===== CHARIZARD - EVOLUÇÃO ESPECIAL ===== */
        @keyframes flame-border {
            0%, 100% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
        }
        
        @keyframes flicker {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.8; }
        }
        
        @keyframes ember-float {
            0% { transform: translateY(0) scale(1); opacity: 1; }
            100% { transform: translateY(-30px) scale(0.5); opacity: 0; }
        }
        
        /* Card especial Charizard */
        .drink-card.type-fire.charizard {
            background: linear-gradient(145deg, 
                rgba(255,69,0,0.15) 0%, 
                rgba(255,140,0,0.1) 50%, 
                rgba(255,69,0,0.15) 100%
            );
            border: 2px solid transparent;
            position: relative;
            overflow: visible;
            transform: scale(1.02);
            margin-top: 10px;
        }
        
        /* Borda flamejante animada */
        .charizard::after {
            content: '';
            position: absolute;
            inset: -3px;
            border-radius: 17px;
            padding: 3px;
            background: linear-gradient(45deg, #ff4500, #ff8c00, #ff4500, #dc143c);
            background-size: 400% 400%;
            animation: flame-border 3s ease infinite;
            -webkit-mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0);
            mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0);
            -webkit-mask-composite: xor;
            mask-composite: exclude;
            z-index: -1;
        }
        
        /* Ícone de fogo no título */
        .drink-name.charizard-name::before {
            content: '🔥 ';
            animation: flicker 1.5s infinite;
        }
        
        /* Indicador de pimenta */
        .spice-level::after {
            content: '🌶️';
            filter: drop-shadow(0 0 5px #ff4500);
            font-size: 1.2em;
        }
        
        /* Brasas */
        .ember {
            position: absolute;
            width: 8px;
            height: 8px;
            background: radial-gradient(circle, #ff8c00 0%, #ff4500 50%, transparent 100%);
            border-radius: 50%;
            pointer-events: none;
            opacity: 0;
        }
        
        .charizard:hover .ember {
            animation: ember-float 1s ease-out infinite;
        }
        
        /* Efeito de calor no hover */
        .charizard:hover {
            transform: translateX(10px) scale(1.03);
            box-shadow: 0 15px 40px rgba(255,69,0,0.4), 0 0 60px rgba(255,140,0,0.2);
        }
        
        /* Charmander mais "básico" para contraste */
        .drink-card.type-fire:not(.charizard) {
            opacity: 0.95;
        }
        
        footer {
            text-align: center;
            margin-top: 40px;
            padding-top: 20px;
            border-top: 2px solid rgba(255, 255, 255, 0.1);
            color: #888;
            font-size: 0.9em;
        }
        
        .trainer-tip {
            background: rgba(255, 203, 5, 0.1);
            border: 2px dashed #ffcb05;
            border-radius: 10px;
            padding: 15px;
            margin-top: 20px;
            text-align: center;
            font-style: italic;
            color: #ffcb05;
        }
        
        @media print {
            body {
                background: #1a1a2e;
                -webkit-print-color-adjust: exact;
                print-color-adjust: exact;
            }
            .container {
                box-shadow: none;
                border: 2px solid #333;
            }
            .drink-card {
                break-inside: avoid;
                page-break-inside: avoid;
            }
        }
        
        @media (max-width: 600px) {
            h1 { font-size: 1.8em; }
            .drink-card { flex-direction: column; text-align: center; }
            .drink-header { justify-content: center; }
            .evolution-badge { 
                top: -8px; 
                right: 50%; 
                transform: translateX(50%);
                font-size: 0.5em;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <div class="pokeball"></div>
           
            <p class="subtitle">Cardápio de Drinks Especiais</p>
        </header>
        
        <div class="menu-grid">
            <!-- Onix - Espresso Martini (BÁSICO) -->
            <div class="drink-card type-rock">
                <img src="https://kimi-web-img.moonshot.cn/img/img.pokemondb.net/2c25ba13688420ab32227c6fedd1951c99ccb55d.png" alt="Onix" class="pokemon-img">
                <div class="drink-info">
                    <div class="drink-header">
                        <span class="drink-type">Tipo Pedra</span>
                        <span class="price">R$ 27</span>
                    </div>
                    <div class="drink-header">
                        <h2 class="drink-name">ONIX</h2>
                    </div>
                    <p class="description">
                        <strong>Espresso Martini</strong><br>
                        Café expresso batido com vodka e licor de café, finalizado com grãos de café. 
                        Forte como o corpo de rocha do Onix!
                    </p>
                </div>
            </div>
            
            <!-- ⛓️ STEELIX - EVOLUÇÃO ⛓️ -->
            <div class="drink-card type-steel steelix">
                <span class="evolution-badge">EVOLUÇÃO!</span>
                
                <img src="https://kimi-web-img.moonshot.cn/img/img.pokemondb.net/04de07080987c4f26571cfe886ab8c149e91a436.png" alt="Steelix" class="pokemon-img">
                
                <div class="drink-info">
                    <div class="drink-header">
                        <span class="drink-type">Tipo Aço ⛓️</span>
                        <span class="price">R$ 30</span>
                    </div>
                    <div class="drink-header">
                        <h2 class="drink-name steelix-name">STEELIX</h2>
                    </div>
                    <p class="description">
                        <strong>Espresso Martini Premium</strong><br>
                        A evolução do Onix! Espresso martini com adição de licor de chocolate meio amargo 
                        e raspas de ouro comestível. <strong>Robusto, sofisticado e inquebrável</strong> como aço!
                    </p>
                </div>
            </div>
            
            <!-- Bulbasaur - Caipirosca de Limão -->
            <div class="drink-card type-grass">
                <img src="https://kimi-web-img.moonshot.cn/img/img.pokemondb.net/748d7aa83dc70756c96ba01b50735994e55d0c27.jpg" alt="Bulbasaur" class="pokemon-img">
                <div class="drink-info">
                    <div class="drink-header">
                        <span class="drink-type">Tipo Grama</span>
                        <span class="price">R$ 20</span>
                    </div>
                    <div class="drink-header">
                        <h2 class="drink-name">BULBASSAURO</h2>
                    </div>
                    <p class="description">
                        <strong>Caipirosca de Limão</strong><br>
                        Vodka, limão fresco, açúcar e gelo. Refrescante como o aroma das flores do bulbo nas costas deste Pokémon.
                    </p>
                </div>
            </div>
            
            <!-- Pikachu - Brasileirinha -->
            <div class="drink-card type-electric">
                <img src="https://kimi-web-img.moonshot.cn/img/img.pokemondb.net/3f7f50afeb428883569447e84157e88b22281470.jpg" alt="Pikachu" class="pokemon-img">
                <div class="drink-info">
                    <div class="drink-header">
                        <span class="drink-type">Tipo Elétrico</span>
                        <span class="price">R$ 25</span>
                    </div>
                    <div class="drink-header">
                        <h2 class="drink-name">PIKACHU</h2>
                    </div>
                    <p class="description">
                        <strong>Brasileirinha</strong><br>
                        Maracujá, limão, açúcar, gelo e vodka. Um choque de sabor tropical! 
                        Eletrificante como um Thunderbolt.
                    </p>
                </div>
            </div>
            
            <!-- Charmander - Caipirosca de Morango (BÁSICO) -->
            <div class="drink-card type-fire">
                <img src="https://kimi-web-img.moonshot.cn/img/img.pokemondb.net/2ae27be9adfd55f331dccda361f5eca87c3f9724.jpg" alt="Charmander" class="pokemon-img">
                <div class="drink-info">
                    <div class="drink-header">
                        <span class="drink-type">Tipo Fogo</span>
                        <span class="price">R$ 23</span>
                    </div>
                    <div class="drink-header">
                        <h2 class="drink-name">CHARMANDER</h2>
                    </div>
                    <p class="description">
                        <strong>Caipirosca de Morango</strong><br>
                        Vodka, morangos frescos, açúcar e gelo.
                        
                    </p>
                </div>
            </div>
            
            <!-- 🔥 CHARIZARD - EVOLUÇÃO 🔥 -->
            <div class="drink-card type-fire charizard">
                <span class="evolution-badge">EVOLUÇÃO!</span>
                <div class="ember" style="left: 20%; top: 80%;"></div>
                <div class="ember" style="left: 50%; top: 85%; animation-delay: 0.3s;"></div>
                <div class="ember" style="left: 80%; top: 80%; animation-delay: 0.6s;"></div>
                
                <img src="https://img.pokemondb.net/artwork/large/charizard.jpg" alt="Charizard" class="pokemon-img">
                
                <div class="drink-info">
                    <div class="drink-header">
                        <span class="drink-type">Tipo Fogo 🔥</span>
                        <span class="price">R$ 25</span>
                    </div>
                    <div class="drink-header">
                        <h2 class="drink-name charizard-name">CHARIZARD</h2>
                        <span class="spice-level" title="Nível de pimenta: Médio"></span>
                    </div>
                    <p class="description">
                        <strong>Caipirosca de Morango Picante</strong><br>
                        A evolução final! Vodka, morangos frescos, açúcar gelo e um 
                        <em>toque de pimenta</em> que incendia o paladar. 
                        Assim como a chama de Charizard, esse drink é <strong>intenso e inesquecível</strong>!
                    </p>
                </div>
            </div>
        </div>
        
        <div class="trainer-tip">
            💡 Dica do Treinador: Evolua seus drinks! Onix → Steelix | Charmander → Charizard
        </div>
        
        <footer>
            
        </footer>
    </div>
</body>
</html>
