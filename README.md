<html lang="id"><head>    <meta charset="UTF-8">    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>TOKO GAMERS - Top Up & Jual Beli Akun</title>
    <meta name="description" content="Toko gamers terlengkap untuk top up game dan jual beli akun game online dari PlayStore">
    <meta name="keywords" content="toko gamers, top up game, jual beli akun game, game online playstore">
    <style>
        /* RESET CSS */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        /* VARIABEL WARNA */
        :root {
            --bg-primary: #00001a;
            --bg-secondary: #000033;
            --bg-card: rgba(0, 0, 51, 0.8);
            --color-primary: #00ccff;
            --color-secondary: #ffcc00;
            --color-success: #25d366;
            --color-text: #ffffff;
            --color-text-light: #b3e0ff;
            --border-radius: 12px;
            --box-shadow: 0 0 20px rgba(0, 204, 255, 0.3);
        }

        /* LATAR BELAKANG LUAR ANGKASA */
        body {
            background: var(--bg-primary);
            color: var(--color-text);
            overflow-x: hidden;
            line-height: 1.6;
        }

        #stars {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 0;
            pointer-events: none;
        }

        .star {
            position: absolute;
            background: white;
            border-radius: 50%;
            animation: twinkle linear infinite;
        }

        @keyframes twinkle {
            0%, 100% { opacity: 0.2; }
            50% { opacity: 1; }
        }

        /* CONTAINER UTAMA */
        .container {
            position: relative;
            z-index: 1;
            width: 95%;
            max-width: 1300px;
            margin: 0 auto;
            padding: 0 10px;
        }

        /* HEADER */
        header {
            background: linear-gradient(to bottom, var(--bg-secondary), transparent);
            padding: 25px 0;
            border-bottom: 2px solid var(--color-primary);
            margin-bottom: 20px;
        }

        .header-content {
            text-align: center;
        }

        header h1 {
            color: var(--color-primary);
            text-shadow: 0 0 15px rgba(0, 204, 255, 0.8);
            font-size: clamp(1.8rem, 5vw, 2.8rem);
            margin-bottom: 8px;
        }

        header p {
            color: var(--color-secondary);
            text-shadow: 0 0 10px rgba(255, 204, 0, 0.6);
            font-size: clamp(0.9rem, 2vw, 1.1rem);
        }

        /* SEARCH SECTION */
        .search-section {
            background: rgba(0, 0, 51, 0.7);
            padding: 20px;
            border-radius: var(--border-radius);
            border: 1px solid var(--color-primary);
            box-shadow: var(--box-shadow);
            margin-bottom: 25px;
            text-align: center;
        }

        #search-input {
            width: clamp(250px, 70%, 500px);
            padding: 12px 15px;
            border-radius: var(--border-radius);
            border: 2px solid var(--color-primary);
            background: var(--bg-secondary);
            color: var(--color-text);
            font-size: 1rem;
            outline: none;
            margin-bottom: 10px;
        }

        #search-input::placeholder {
            color: var(--color-text-light);
        }

        #search-btn {
            padding: 12px 25px;
            background: linear-gradient(to right, var(--color-primary), #0066ff);
            color: var(--bg-secondary);
            border: none;
            border-radius: var(--border-radius);
            font-weight: 600;
            cursor: pointer;
            box-shadow: 0 0 15px rgba(0, 204, 255, 0.5);
            transition: transform 0.3s ease;
            font-size: 1rem;
        }

        #search-btn:hover {
            transform: scale(1.05);
        }

        /* FILTER SECTION */
        .filter-section {
            margin-bottom: 25px;
            overflow-x: auto;
            white-space: nowrap;
            padding: 10px 0;
            scrollbar-width: thin;
            scrollbar-color: var(--color-primary) var(--bg-secondary);
        }

        .filter-section::-webkit-scrollbar {
            height: 6px;
        }

        .filter-section::-webkit-scrollbar-track {
            background: var(--bg-secondary);
            border-radius: 10px;
        }

        .filter-section::-webkit-scrollbar-thumb {
            background: var(--color-primary);
            border-radius: 10px;
        }

        .filter-btn {
            background: rgba(0, 0, 51, 0.7);
            color: var(--color-text-light);
            border: 1px solid var(--color-primary);
            padding: 8px 18px;
            border-radius: 8px;
            margin: 0 5px;
            cursor: pointer;
            transition: all 0.3s ease;
            font-size: clamp(0.8rem, 2vw, 0.95rem);
            white-space: nowrap;
        }

        .filter-btn:hover, .filter-btn.active {
            background: var(--color-primary);
            color: var(--bg-secondary);
            font-weight: 600;
        }

        /* GAME CARDS SECTION */
        .games-section {
            margin-bottom: 40px;
        }

        .games-section h2 {
            text-align: center;
            color: var(--color-primary);
            text-shadow: 0 0 15px rgba(0, 204, 255, 0.8);
            font-size: clamp(1.5rem, 3vw, 1.8rem);
            margin-bottom: 25px;
        }

        .game-cards {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(clamp(140px, 25%, 200px), 1fr));
            gap: 20px;
        }

        .card {
            background: var(--bg-card);
            padding: 18px;
            border-radius: var(--border-radius);
            text-align: center;
            cursor: pointer;
            transition: all 0.3s ease;
            border: 2px solid transparent;
            box-shadow: 0 0 15px rgba(0, 0, 0, 0.5);
        }

        .card:hover {
            transform: translateY(-8px);
            border-color: var(--color-secondary);
            box-shadow: 0 0 25px rgba(255, 204, 0, 0.5);
        }

        .card img {
            width: clamp(60px, 50%, 80px);
            height: clamp(60px, 50%, 80px);
            margin-bottom: 15px;
            border-radius: 50%;
            border: 3px solid var(--color-primary);
            box-shadow: 0 0 15px rgba(0, 204, 255, 0.7);
        }

        .card h3 {
            color: var(--color-secondary);
            text-shadow: 0 0 10px rgba(255, 204, 0, 0.6);
            font-size: clamp(0.8rem, 2vw, 0.95rem);
            line-height: 1.3;
        }

        /* ORDER FORM SECTION */
        .order-form {
            background: var(--bg-card);
            padding: 25px;
            border-radius: var(--border-radius);
            border: 2px solid var(--color-primary);
            box-shadow: var(--box-shadow);
            margin-bottom: 30px;
            display: none;
        }

        .order-form h2 {
            text-align: center;
            color: var(--color-secondary);
            text-shadow: 0 0 15px rgba(255, 204, 0, 0.7);
            font-size: clamp(1.3rem, 3vw, 1.6rem);
            margin-bottom: 20px;
        }

        .form-group {
            margin-bottom: 18px;
        }

        label {
            display: block;
            color: var(--color-primary);
            font-size: clamp(0.9rem, 2vw, 1rem);
            margin-bottom: 8px;
            font-weight: 500;
        }

        input, select {
            width: 100%;
            padding: 12px;
            border-radius: 8px;
            border: 2px solid var(--color-primary);
            background: var(--bg-secondary);
            color: var(--color-text);
            font-size: 1rem;
            outline: none;
        }

        input::placeholder {
            color: var(--color-text-light);
        }

        .price-wrapper {
            display: flex;
            align-items: center;
        }

        .price-prefix {
            background: var(--bg-secondary);
            color: var(--color-text-light);
            padding: 12px 15px;
            border: 2px solid var(--color-primary);
            border-right: none;
            border-top-left-radius: 8px;
            border-bottom-left-radius: 8px;
            font-size: 1rem;
        }

        #total_harga {
            border-top-left-radius: 0;
            border-bottom-left-radius: 0;
        }

        #buy-btn {
            width: 100%;
            padding: 15px;
            background: linear-gradient(to right, var(--color-secondary), #ff9900);
            color: var(--bg-secondary);
            border: none;
            border-radius: 8px;
            font-size: clamp(1rem, 2vw, 1.2rem);
            font-weight: 600;
            cursor: pointer;
            box-shadow: 0 0 20px rgba(255, 204, 0, 0.6);
            transition: all 0.3s ease;
            margin-top: 10px;
        }

        #buy-btn:hover {
            transform: scale(1.02);
            box-shadow: 0 0 25px rgba(255, 204, 0, 0.8);
        }

        /* ORDER RESULT SECTION */
        .order-result {
            background: rgba(0, 34, 102, 0.9);
            padding: 25px;
            border-radius: var(--border-radius);
            border: 2px solid var(--color-secondary);
            box-shadow: 0 0 25px rgba(255, 204, 0, 0.5);
            text-align: center;
            margin-bottom: 30px;
            display: none;
        }

        .order-result h3 {
            color: var(--color-primary);
            text-shadow: 0 0 15px rgba(0, 204, 255, 0.8);
            font-size: clamp(1.2rem, 3vw, 1.5rem);
            margin-bottom: 20px;
        }

        #order-id {
            font-size: clamp(1.3rem, 3vw, 1.8rem);
            font-weight: 700;
            color: var(--color-secondary);
            text-shadow: 0 0 15px rgba(255, 204, 0, 0.8);
            margin: 15px 0;
        }

        .whatsapp-link {
            color: var(--color-success);
            text-decoration: none;
            font-weight: 600;
            font-size: clamp(1rem, 2vw, 1.2rem);
            text-shadow: 0 0 10px rgba(37, 211, 102, 0.7);
        }

        .whatsapp-link:hover {
            text-decoration: underline;
        }

        /* FOOTER */
        footer {
            background: linear-gradient(to top, var(--bg-secondary), transparent);
            padding: 20px 0;
            border-top: 2px solid var(--color-primary);
            text-align: center;
        }

        footer p {
            color: var(--color-text-light);
            font-size: clamp(0.8rem, 2vw, 0.95rem);
        }

        /* CLASS UNTUK MENYEMBUNYIKAN ELEMEN */
        .hide {
            display: none !important;
        }

        /* RESPONSIF KHUSUS HP (LEBIH KECIL DARI 480PX) */
        @media (max-width: 480px) {
            .search-section {
                padding: 15px;
            }

            .filter-btn {
                padding: 6px 12px;
                margin: 0 3px;
            }

            .game-cards {
                gap: 15px;
            }

            .card {
                padding: 15px;
            }

            .order-form, .order-result {
                padding: 20px;
            }
        }
    </style>
</head>
<body>
    <!-- LATAR BELAKANG BINTANG -->
    <div id="stars"></div>

    <!-- HEADER -->
    <header>
        <div class="container header-content">
            <h1>TOKO GAMERS</h1>
            <p>Top Up & Jual Beli Akun Game Online Terlengkap!</p>
        </div>
    </header>

    <!-- MAIN CONTENT -->
    <main class="container">
        <!-- SEARCH SECTION -->
        <section class="search-section">
            <input type="text" id="search-input" placeholder="Cari game (contoh: Mobile Legends, Free Fire)...">
            <button id="search-btn">CARI GAME</button>
        </section>

        <!-- FILTER SECTION -->
        <section class="filter-section">
            <button class="filter-btn active" data-filter="all">SEMUA GAME</button>
            <button class="filter-btn" data-filter="moba">MOBA</button>
            <button class="filter-btn" data-filter="battle-royale">BATTLE ROYALE</button>
            <button class="filter-btn" data-filter="sports">SPORT</button>
            <button class="filter-btn" data-filter="mmorpg">MMORPG</button>
            <button class="filter-btn" data-filter="card">CARD GAME</button>
            <button class="filter-btn" data-filter="strategy">STRATEGI</button>
            <button class="filter-btn" data-filter="other">LAINNYA</button>
        </section>

        <!-- GAME CARDS SECTION -->
        <section class="games-section">
            <h2>KUMPULAN GAME ONLINE GALAKSI</h2>
            <div class="game-cards" id="game-cards">
                <!-- ====================== MOBA ====================== -->
                <div class="card" data-game="Mobile Legends: Bang Bang" data-category="moba">
                    <img src="https://cdn-icons-png.flaticon.com/512/5968/5968705.png" alt="Mobile Legends">
                    <h3>MOBILE LEGENDS</h3>
                </div>
                <div class="card" data-game="Honor of Kings" data-category="moba">
                    <img src="https://cdn-icons-png.flaticon.com/512/4154/4154533.png" alt="Honor of Kings">
                    <h3>HONOR OF KINGS</h3>
                </div>
                <div class="card" data-game="League of Legends: Wild Rift" data-category="moba">
                    <img src="https://cdn-icons-png.flaticon.com/512/6062/6062741.png" alt="LOL Wild Rift">
                    <h3>LOL WILD RIFT</h3>
                </div>
                <div class="card" data-game="Arena of Valor" data-category="moba">
                    <img src="https://cdn-icons-png.flaticon.com/512/4154/4154525.png" alt="Arena of Valor">
                    <h3>ARENA OF VALOR</h3>
                </div>
                <div class="card" data-game="Vainglory" data-category="moba">
                    <img src="https://cdn-icons-png.flaticon.com/512/4154/4154542.png" alt="Vainglory">
                    <h3>VAINGLORY</h3>
                </div>

                <!-- ====================== BATTLE ROYALE ====================== -->
                <div class="card" data-game="Free Fire" data-category="battle-royale">
                    <img src="https://cdn-icons-png.flaticon.com/512/6035/6035774.png" alt="Free Fire">
                    <h3>FREE FIRE</h3>
                </div>
                <div class="card" data-game="PUBG Mobile" data-category="battle-royale">
                    <img src="https://cdn-icons-png.flaticon.com/512/6062/6062659.png" alt="PUBG Mobile">
                    <h3>PUBG MOBILE</h3>
                </div>
                <div class="card" data-game="Fortnite Mobile" data-category="battle-royale">
                    <img src="https://cdn-icons-png.flaticon.com/512/5968/5968715.png" alt="Fortnite">
                    <h3>FORTNITE MOBILE</h3>
                </div>
                <div class="card" data-game="Call of Duty: Mobile" data-category="battle-royale">
                    <img src="https://cdn-icons-png.flaticon.com/512/6062/6062663.png" alt="COD Mobile">
                    <h3>COD MOBILE</h3>
                </div>
                <div class="card" data-game="Apex Legends Mobile" data-category="battle-royale">
                    <img src="https://cdn-icons-png.flaticon.com/512/6062/6062660.png" alt="Apex Legends">
                    <h3>APEX LEGENDS</h3>
                </div>

                <!-- ====================== SPORT ====================== -->
                <div class="card" data-game="FC Mobile (FIFA Mobile)" data-category="sports">
                    <img src="https://cdn-icons-png.flaticon.com/512/281/281669.png" alt="FC Mobile">
                    <h3>FC MOBILE</h3>
                </div>
                <div class="card" data-game="eFootball PES Mobile" data-category="sports">
                    <img src="https://cdn-icons-png.flaticon.com/512/5968/5968725.png" alt="eFootball">
                    <h3>EFOOTBALL PES</h3>
                </div>
                <div class="card" data-game="NBA 2K Mobile" data-category="sports">
                    <img src="https://cdn-icons-png.flaticon.com/512/5968/5968728.png" alt="NBA 2K">
                    <h3>NBA 2K MOBILE</h3>
                </div>
                <div class="card" data-game="Real Cricket 24" data-category="sports">
                    <img src="https://cdn-icons-png.flaticon.com/512/5968/5968730.png" alt="Real Cricket">
                    <h3>REAL CRICKET 24</h3>
                </div>
                <div class="card" data-game="Golf Clash" data-category="sports">
                    <img src="https://cdn-icons-png.flaticon.com/512/5968/5968732.png" alt="Golf Clash">
                    <h3>GOLF CLASH</h3>
                </div>

                <!-- ====================== MMORPG ====================== -->
                <div class="card" data-game="Genshin Impact" data-category="mmorpg">
                    <img src="https://cdn-icons-png.flaticon.com/512/6062/6062667.png" alt="Genshin Impact">
                    <h3>GENSHIN IMPACT</h3>
                </div>
                <div class="card" data-game="Honkai: Star Rail" data-category="mmorpg">
                    <img src="https://cdn-icons-png.flaticon.com/512/6062/6062668.png" alt="Honkai Star Rail">
                    <h3>HONKAI STAR RAIL</h3>
                </div>
                <div class="card" data-game="Black Desert Mobile" data-category="mmorpg">
                    <img src="https://cdn-icons-png.flaticon.com/512/4154/4154527.png" alt="Black Desert">
                    <h3>BLACK DESERT</h3>
                </div>
                <div class="card" data-game="Lineage 2 Revolution" data-category="mmorpg">
                    <img src="https://cdn-icons-png.flaticon.com/512/4154/4154535.png" alt="Lineage 2">
                    <h3>LINEAGE 2 REVOLUTION</h3>
                </div>
                <div class="card" data-game="Ragnarok M: Eternal Love" data-category="mmorpg">
                    <img src="https://cdn-icons-png.flaticon.com/512/4154/4154538.png" alt="Ragnarok M">
                    <h3>RAGNAROK M ETERNAL LOVE</h3>
                </div>

                <!-- ====================== CARD GAME ====================== -->
                <div class="card" data-game="Yu-Gi-Oh! Duel Links" data-category="card">
                    <img src="https://cdn-icons-png.flaticon.com/512/5968/5968740.png" alt="Yu-Gi-Oh">
                    <h3>YU-GI-OH! DUEL LINKS</h3>
                </div>
                <div class="card" data-game="Hearthstone" data-category="card">
                    <img src="https://cdn-icons-png.flaticon.com/512/5968/5968742.png" alt="Hearthstone">
                    <h3>HEARTHSTONE</h3>
                </div>
                <div class="card" data-game="Magic: The Gathering Arena" data-category="card">
                    <img src="https://cdn-icons-png.flaticon.com/512/5968/5968745.png" alt="Magic The Gathering">
                    <h3>MAGIC THE GATHERING</h3>
                </div>
                <div class="card" data-game="Shadowverse CCG" data-category="card">
                    <img src="https://cdn-icons-png.flaticon.com/512/5968/5968747.png" alt="Shadowverse">
                    <h3>SHADOWVERSE CCG</h3>
                </div>
                <div class="card" data-game="Pokémon TCG Online" data-category="card">
                    <img src="https://cdn-icons-png.flaticon.com/512/5968/5968750.png" alt="Pokemon TCG">
                    <h3>POKEMON TCG ONLINE</h3>
                </div>

                <!-- ====================== STRATEGI ====================== -->
                <div class="card" data-game="Clash of Clans" data-category="strategy">
                    <img src="https://cdn-icons-png.flaticon.com/512/5968/5968755.png" alt="Clash of Clans">
                    <h3>CLASH OF CLANS</h3>
                </div>
                <div class="card" data-game="Clash Royale" data-category="strategy">
                    <img src="https://cdn-icons-png.flaticon.com/512/5968/5968757.png" alt="Clash Royale">
                    <h3>CLASH ROYALE</h3>
                </div>
                <div class="card" data-game="Age of Empires Mobile" data-category="strategy">
                    <img src="https://cdn-icons-png.flaticon.com/512/5968/5968760.png" alt="Age of Empires">
                    <h3>AGE OF EMPIRES MOBILE</h3>
                </div>
                <div class="card" data-game="Rise of Kingdoms" data-category="strategy">
                    <img src="https://cdn-icons-png.flaticon.com/512/5968/5968762.png" alt="Rise of Kingdoms">
                    <h3>RISE OF KINGDOMS</h3>
                </div>
                <div class="card" data-game="Mobile Strike" data-category="strategy">
                    <img src="https://cdn-icons-png.flaticon.com/512/5968/5968765.png" alt="Mobile Strike">
                    <h3>MOBILE STRIKE</h3>
                </div>

                <!-- ====================== LAINNYA ====================== -->
                <div class="card" data-game="Roblox" data-category="other">
                    <img src="https://cdn-icons-png.flaticon.com/512/5968/5968770.png" alt="Roblox">
                    <h3>ROBLOX</h3>
                </div>
                <div class="card" data-game="Minecraft" data-category="other">
                    <img src="https://cdn-icons-png.flaticon.com/512/5968/5968772.png" alt="Minecraft">
                    <h3>MINECRAFT</h3>
                </div>
                <div class="card" data-game="Subway Surfers" data-category="other">
                    <img src="https://cdn-icons-png.flaticon.com/512/5968/5968775.png" alt="Subway Surfers">
                    <h3>SUBWAY SURFERS</h3>
                </div>
                <div class="card" data-game="Candy Crush Saga" data-category="other">
                    <img src="https://cdn-icons-png.flaticon.com/512/5968/5968777.png" alt="Candy Crush">
                    <h3>CANDY CRUSH SAGA</h3>
                </div>
                <div class="card" data-game="Among Us" data-category="other">
                    <img src="https://cdn-icons-png.flaticon.com/512/5968/5968780.png" alt="Among Us">
                    <h3>AMONG US</h3>
                </div>
            </div>
        </section>

        <!-- ORDER FORM -->
        <section class="order-form" id="order-form">
            <h2>FORM PEMESANAN</h2>
            <form id="gamer-order-form">
                <input type="hidden" name="id_pesanan" id="hidden-order-id">

                <div class="form-group">
                    <label>Nama Pembeli:</label>
                    <input type="text" name="nama_pembeli" required placeholder="Masukkan nama lengkap Anda">
                </div>

                <div class="form-group">
                    <label>ID/Username Akun Game:</label>
                    <input type="text" name="id_game" required placeholder="Masukkan ID atau username game Anda">
                </div>

                <div class="form-group">
                    <label>Nama Game:</label>
                    <select name="kategori_game" id="game-select" required>
                        <option value="">Pilih game yang ingin Anda pesan</option>
                        <option value="Mobile Legends: Bang Bang">Mobile Legends: Bang Bang</option>
                        <option value="Honor of Kings">Honor of Kings</option>
                        <option value="League of Legends: Wild Rift">League of Legends: Wild Rift</option>
                        <option value="Arena of Valor
