<html lang="id"><head>    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>TOKO GAMERS - Luar Angkasa</title>
    <style>
        /* Style tetap sama seperti sebelumnya (saya ringkas) */
        * { margin:0; padding:0; box-sizing:border-box; font-family:'Arial',sans-serif; }
        body { background:#00001a; color:white; overflow-x:hidden; }
        #stars { position:fixed; top:0; left:0; width:100%; height:100%; z-index:0; }
        .star { position:absolute; background:white; border-radius:50%; animation:twinkle 4s linear infinite; }

        @keyframes twinkle { 0%,100% {opacity:0.3;} 50% {opacity:1;} }

        header {
            position:relative; z-index:10; background:linear-gradient(to bottom,#000033,transparent);
            padding:15px 20px; display:flex; justify-content:space-between; align-items:center;
            border-bottom:2px solid #00ccff;
        }

        .login-status { display:flex; align-items:center; gap:12px; font-size:0.95rem; }
        #user-email { color:#00ffcc; font-weight:bold; }
        
        button {
            padding:10px 18px; border:none; border-radius:8px; cursor:pointer; font-weight:bold;
        }
        #login-btn { background:linear-gradient(#00ccff,#0066ff); color:white; }
        #logout-btn { background:#ff4444; color:white; }
    </style>
</head>
<body>
    <div id="stars"></div>

    <header>
        <div>
            <h1 style="color:#00ccff; font-size:2.3rem;">TOKO GAMERS</h1>
            <p style="color:#ffcc00;">Luar Angkasa</p>
        </div>
        <div class="login-status">
            <span id="user-email" style="display:none;"></span>
            <button id="login-btn">Login Email</button>
            <button id="logout-btn" style="display:none;">Logout</button>
        </div>
    </header>

    <!-- Search & Game Cards (sama seperti sebelumnya) -->
    <div class="search-section" style="text-align:center; padding:25px; background:rgba(0,0,51,0.7); margin:20px auto; max-width:800px; border-radius:15px; border:1px solid #00ccff;">
        <input type="text" id="search-input" placeholder="Cari game..." style="width:70%; padding:15px; border-radius:8px; border:2px solid #00ccff; background:rgba(0,0,34,0.9); color:white;">
        <button id="search-btn" style="padding:15px 30px; background:linear-gradient(#00ccff,#0066ff); color:white; border:none; border-radius:8px;">CARI</button>
    </div>

    <div class="categories-section" style="padding:20px; text-align:center;">
        <h2 style="color:#00ccff; margin-bottom:25px;">KATEGORI GAME</h2>
        <div id="game-cards" style="display:grid; grid-template-columns:repeat(auto-fit, minmax(180px,1fr)); gap:20px; max-width:1200px; margin:0 auto;"></div>
    </div>

    <!-- LOGIN MODAL -->
    <div id="login-modal" style="display:none; position:fixed; top:0; left:0; width:100%; height:100%; background:rgba(0,0,0,0.95); z-index:1000; align-items:center; justify-content:center;">
        <div style="background:#000033; padding:40px; border-radius:20px; border:3px solid #00ccff; width:90%; max-width:420px; text-align:center;">
            <h2 style="color:#00ccff; margin-bottom:20px;">Masuk dengan Email</h2>
            <input type="email" id="login-email-input" placeholder="contoh@email.com" 
                   style="width:100%; padding:15px; margin:15px 0; border-radius:10px; border:2px solid #00ccff; background:#000022; color:white; font-size:16px;">
            <button id="confirm-login" style="width:100%; padding:15px; background:linear-gradient(#00ccff,#0066ff); color:white; border:none; border-radius:10px; font-size:1.1rem; margin-top:10px;">
                LOGIN
            </button>
            <button id="cancel-login" style="width:100%; padding:12px; background:#444; color:white; border:none; border-radius:10px; margin-top:10px;">Batal</button>
        </div>
    </div>

    <!-- Order Form -->
    <div id="order-form" class="order-form-section" style="display:none; max-width:650px; margin:30px auto; padding:30px; background:rgba(0,0,51,0.9); border:2px solid #00ccff; border-radius:15px;">
        <h2 style="text-align:center; color:#ffcc00;">Form Pemesanan</h2>
        <form id="orderForm">
            <input type="hidden" id="hidden-order-id" name="id_pesanan">
            
            <div class="form-group"><label>Nama Pembeli</label><input type="text" name="nama_pembeli" required></div>
            <div class="form-group"><label>ID Game</label><input type="text" name="id_game" required></div>
            
            <div class="form-group">
                <label>Game</label>
                <select id="game-category" name="kategori_game" required style="width:100%; padding:12px;"></select>
            </div>

            <div class="form-group"><label>Jenis Layanan</label>
                <select name="jenis_produk" required>
                    <option value="Top Up">Top Up</option>
                    <option value="Beli Akun">Beli Akun</option>
                    <option value="Jual Akun">Jual Akun</option>
                </select>
            </div>

            <div class="form-group"><label>Total Harga (Rp)</label><input type="number" name="total_harga" required></div>
            
            <div class="form-group">
                <label>Email Konfirmasi</label>
                <input type="email" id="email_pembeli" name="email_pembeli" readonly>
            </div>

            <button type="submit" id="buy-btn" style="width:100%; padding:18px; background:linear-gradient(#ffcc00,#ff9900); color:#000; font-size:1.2rem; border:none; border-radius:10px; margin-top:15px;">
                BAYAR SEKARANG
            </button>
        </form>
    </div>

    <script>
        // EmailJS (tetap)
        emailjs.init("gjZHP31_wCsPbE4XH");

        // Daftar Game
        const games = ["FC MOBILE","MOBILE LEGENDS","FREE FIRE","PUBG MOBILE","HONOR OF KINGS","GENSHIN IMPACT","ROBLOX","BRAWL STARS","CALL OF DUTY MOBILE","CLASH OF CLANS","MINECRAFT","STUMBLE GUYS","UNDISPUTED","VALORANT","HONKAI STAR RAIL"];

        // Buat bintang
        function createStars() {
            const stars = document.getElementById('stars');
            for (let i = 0; i < 280; i++) {
                const star = document.createElement('div');
                star.className = 'star';
                star.style.width = star.style.height = Math.random() * 3 + 1 + 'px';
                star.style.left = Math.random() * 100 + '%';
                star.style.top = Math.random() * 100 + '%';
                star.style.animationDuration = (Math.random() * 4 + 3) + 's';
                stars.appendChild(star);
            }
        }

        let currentEmail = localStorage.getItem('tokogamers_email');

        function updateUI() {
            if (currentEmail) {
                document.getElementById('user-email').textContent = currentEmail;
                document.getElementById('user-email').style.display = 'inline';
                document.getElementById('login-btn').style.display = 'none';
                document.getElementById('logout-btn').style.display = 'inline';
            }
        }

        // Login
        document.getElementById('login-btn').onclick = () => {
            document.getElementById('login-modal').style.display = 'flex';
        };

        document.getElementById('confirm-login').onclick = () => {
            const emailInput = document.getElementById('login-email-input').value.trim();
            if (emailInput.includes('@') && emailInput.includes('.')) {
                currentEmail = emailInput;
                localStorage.setItem('tokogamers_email', emailInput);
                updateUI();
                document.getElementById('login-modal').style.display = 'none';
                document.getElementById('email_pembeli').value = emailInput;
                alert('✅ Login berhasil! Selamat berbelanja di Toko Gamers.');
            } else {
                alert('Masukkan email yang valid!');
            }
        };

        document.getElementById('cancel-login').onclick = () => {
            document.getElementById('login-modal').style.display = 'none';
        };

        document.getElementById('logout-btn').onclick = () => {
            localStorage.removeItem('tokogamers_email');
            currentEmail = null;
            location.reload();
        };

        // Generate Cards & Select
        function initGames() {
            const container = document.getElementById('game-cards');
            const select = document.getElementById('game-category');
            
            games.forEach(game => {
                // Card
                const card = document.createElement('div');
                card.style.cssText = `background:rgba(0,0,51,0.85); padding:20px; border-radius:15px; text-align:center; cursor:pointer; border:2px solid transparent; transition:0.3s;`;
                card.innerHTML = `<h3 style="color:#ffcc00;">${game}</h3>`;
                card.onclick = () => {
                    if (!currentEmail) {
                        alert('⚠️ Silakan login terlebih dahulu!');
                        document.getElementById('login-modal').style.display = 'flex';
                        return;
                    }
                    document.getElementById('game-category').value = game;
                    document.getElementById('order-form').style.display = 'block';
                    document.getElementById('order-form').scrollIntoView({behavior:'smooth'});
                };
                container.appendChild(card);

                // Select option
                const opt = document.createElement('option');
                opt.value = game;
                opt.textContent = game;
                select.appendChild(opt);
            });
        }

        // Form Submit
        document.getElementById('orderForm').onsubmit = function(e) {
            e.preventDefault();
            if (!currentEmail) {
                alert("Silakan login terlebih dahulu!");
                return;
            }

            const orderId = "GALAXY-" + Math.random().toString(36).substr(2,9).toUpperCase();
            document.getElementById('hidden-order-id').value = orderId;

            emailjs.sendForm('service_u5bjqpt', 'template_tdfja1m', this)
                .then(() => {
                    alert(`✅ Pesanan berhasil! ID: ${orderId}\nSilakan hubungi admin via WhatsApp.`);
                    this.reset();
                    document.getElementById('order-form').style.display = 'none';
                })
                .catch(err => alert('Gagal mengirim. Coba lagi.'));
        };

        // Search
        document.getElementById('search-btn').onclick = () => {
            const term = document.getElementById('search-input').value.toLowerCase();
            document.querySelectorAll('#game-cards > div').forEach(card => {
                card.style.display = card.textContent.toLowerCase().includes(term) ? 'block' : 'none';
            });
        };

        // Init
        window.onload = () => {
            createStars();
            initGames();
            updateUI();
            if (currentEmail) document.getElementById('email_pembeli').value = currentEmail;
        };
    </script>
</body>
</html>
