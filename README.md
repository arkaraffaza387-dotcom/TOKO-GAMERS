<html lang="id"><head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>TOKO GAMERS - Luar Angkasa</title>
    <style>
        * { margin:0; padding:0; box-sizing:border-box; font-family:'Arial',sans-serif; }
        body { background:#00001a; color:white; overflow-x:hidden; }
        #stars { position:fixed; top:0; left:0; width:100%; height:100%; z-index:0; }
        .star { position:absolute; background:white; border-radius:50%; animation:twinkle linear infinite; }
        @keyframes twinkle { 0%,100%{opacity:0.3} 50%{opacity:1} }

        header {
            position:relative; z-index:10; background:linear-gradient(to bottom,#000033,transparent);
            padding:20px; display:flex; justify-content:space-between; align-items:center;
            border-bottom:2px solid #00ccff;
        }
        .header-left h1 { color:#00ccff; font-size:2.4rem; text-shadow:0 0 15px rgba(0,204,255,0.8); }
        .header-left p { color:#ffcc00; }

        .register-status { display:flex; align-items:center; gap:15px; }
        #register-info { color:#00ffcc; font-weight:bold; }
        button { padding:10px 20px; border:none; border-radius:8px; cursor:pointer; font-weight:bold; }
        #register-btn { background:linear-gradient(#00ccff,#0066ff); color:white; }
        #logout-btn { background:#ff4444; color:white; }

        .search-section, .categories-section, .order-form-section {
            position:relative; z-index:1;
        }
        .search-section { padding:25px; text-align:center; background:rgba(0,0,51,0.7); margin:20px auto; max-width:800px; border-radius:15px; border:1px solid #00ccff; }
        #search-input { width:70%; padding:15px; border:2px solid #00ccff; background:rgba(0,0,34,0.9); color:white; border-radius:8px; }
        #search-btn { padding:15px 30px; background:linear-gradient(#00ccff,#0066ff); color:white; border:none; border-radius:8px; }

        .game-cards { display:grid; grid-template-columns:repeat(auto-fit, minmax(180px,1fr)); gap:20px; padding:20px; }
        .card {
            background:rgba(0,0,51,0.85); padding:20px; border-radius:15px; text-align:center;
            cursor:pointer; transition:0.3s; border:2px solid transparent;
        }
        .card:hover { transform:translateY(-8px); border-color:#ffcc00; }

        .order-form-section {
            max-width:650px; margin:30px auto; padding:30px; background:rgba(0,0,51,0.9);
            border-radius:15px; border:2px solid #00ccff; display:none;
        }
        .form-group { margin-bottom:20px; }
        label { display:block; margin-bottom:8px; color:#00ccff; }
        input, select {
            width:100%; padding:12px; border-radius:8px; border:2px solid #00ccff;
            background:rgba(0,0,34,0.9); color:white;
        }
        #buy-btn {
            width:100%; padding:18px; background:linear-gradient(#ffcc00,#ff9900);
            color:#000; border:none; border-radius:8px; font-size:1.2rem; font-weight:bold;
        }
    </style>
</head>
<body>
    <div id="stars"></div>

    <header>
        <div class="header-left">
            <h1>TOKO GAMERS</h1>
            <p>Luar Angkasa</p>
        </div>
        <div class="register-status">
            <span id="register-info"></span>
            <button id="register-btn">Register</button>
            <button id="logout-btn" style="display:none;">Logout</button>
        </div>
    </header>

    <div class="search-section">
        <input type="text" id="search-input" placeholder="Cari game...">
        <button id="search-btn">CARI</button>
    </div>

    <div class="categories-section">
        <h2 style="text-align:center; color:#00ccff; margin-bottom:25px;">KATEGORI GAME GALAKSI</h2>
        <div class="game-cards" id="game-cards"></div>
    </div>

    <!-- Register Modal -->
    <div id="register-modal" style="display:none; position:fixed; top:0; left:0; width:100%; height:100%; background:rgba(0,0,0,0.95); z-index:1000; align-items:center; justify-content:center;">
        <div style="background:#000033; padding:40px; border-radius:15px; border:3px solid #00ccff; width:90%; max-width:420px;">
            <h2 style="text-align:center; color:#00ccff;">Register Akun</h2>
            <input type="text" id="reg-name" placeholder="Nama Lengkap" style="width:100%; padding:14px; margin:10px 0; border:2px solid #00ccff; background:#000022; color:white; border-radius:8px;">
            <input type="email" id="reg-email" placeholder="Email Anda" style="width:100%; padding:14px; margin:10px 0; border:2px solid #00ccff; background:#000022; color:white; border-radius:8px;">
            <button id="confirm-register" style="width:100%; padding:15px; background:linear-gradient(#00ccff,#0066ff); color:white; border:none; border-radius:8px; margin-top:15px;">DAFTAR SEKARANG</button>
            <button id="cancel-register" style="width:100%; padding:12px; background:#555; color:white; border:none; border-radius:8px; margin-top:10px;">Batal</button>
        </div>
    </div>

    <!-- Form Pesanan -->
    <div class="order-form-section" id="order-form">
        <h2 style="text-align:center; color:#ffcc00;">FORM PEMESANAN</h2>
        <form id="orderForm">
            <input type="hidden" name="id_pesanan" id="hidden-order-id">

            <div class="form-group">
                <label>Nama Pembeli</label>
                <input type="text" name="nama_pembeli" id="nama_pembeli" required>
            </div>
            <div class="form-group">
                <label>ID/Username Game</label>
                <input type="text" name="id_game" id="id_game" required>
            </div>
            <div class="form-group">
                <label>Kategori Game</label>
                <select name="kategori_game" id="game-category" required></select>
            </div>
            <div class="form-group">
                <label>Jenis Produk</label>
                <select name="jenis_produk" id="jenis_produk" required>
                    <option value="">Pilih</option>
                    <option value="Top Up">Top Up</option>
                    <option value="Beli Akun">Beli Akun</option>
                    <option value="Jual Akun">Jual Akun</option>
                </select>
            </div>
            <div class="form-group">
                <label>Total Harga (Rp)</label>
                <input type="number" name="total_harga" id="total_harga" required>
            </div>
            <div class="form-group">
                <label>Email Pembeli</label>
                <input type="email" name="email_pembeli" id="email_pembeli" readonly>
            </div>

            <button type="submit" id="buy-btn">BAYAR SEKARANG</button>
        </form>
    </div>

    <!-- Hasil -->
    <div id="order-result" class="order-result" style="display:none; text-align:center; max-width:650px; margin:30px auto; padding:30px; background:rgba(0,34,102,0.9); border:2px solid #ffcc00; border-radius:15px;">
        <h3>✅ PEMESANAN BERHASIL!</h3>
        <p>ID Pesanan: <span id="order-id" style="color:#ffcc00; font-size:1.6rem;"></span></p>
        <p>Detail pesanan sudah dikirim ke email admin.</p>
    </div>

    <script src="https://cdn.jsdelivr.net/npm/emailjs-com@3/dist/email.min.js"></script>
    <script>
        emailjs.init("gjZHP31_wCsPbE4XH");

        const games = ["FC MOBILE","MOBILE LEGENDS","FREE FIRE","PUBG MOBILE","HONOR OF KINGS","GENSHIN IMPACT","ROBLOX","BRAWL STARS","CALL OF DUTY MOBILE","CLASH OF CLANS","MINECRAFT","STUMBLE GUYS","VALORANT","HONKAI STAR RAIL","UNDISPUTED"];

        let userData = JSON.parse(localStorage.getItem('tokogamers_user')) || null;

        function createStars() {
            const container = document.getElementById('stars');
            for (let i = 0; i < 280; i++) {
                const star = document.createElement('div');
                star.className = 'star';
                const size = Math.random() * 3 + 1;
                star.style.width = star.style.height = `${size}px`;
                star.style.left = `${Math.random()*100}%`;
                star.style.top = `${Math.random()*100}%`;
                star.style.animationDuration = `${Math.random()*5 + 3}s`;
                container.appendChild(star);
            }
        }

        function updateUI() {
            if (userData) {
                document.getElementById('register-info').textContent = `👤 ${userData.name}`;
                document.getElementById('register-info').style.display = 'inline';
                document.getElementById('register-btn').style.display = 'none';
                document.getElementById('logout-btn').style.display = 'inline';
                document.getElementById('email_pembeli').value = userData.email;
            }
        }

        function generateGames() {
            const container = document.getElementById('game-cards');
            const select = document.getElementById('game-category');
            games.forEach(game => {
                const card = document.createElement('div');
                card.className = 'card';
                card.innerHTML = `<h3>${game}</h3>`;
                card.onclick = () => {
                    if (!userData) {
                        alert("Silakan Register terlebih dahulu!");
                        document.getElementById('register-modal').style.display = 'flex';
                        return;
                    }
                    document.getElementById('game-category').value = game;
                    document.getElementById('order-form').style.display = 'block';
                    document.getElementById('order-form').scrollIntoView({behavior:'smooth'});
                };
                container.appendChild(card);

                const opt = document.createElement('option');
                opt.value = game; opt.textContent = game;
                select.appendChild(opt);
            });
        }

        // Register
        document.getElementById('register-btn').onclick = () => document.getElementById('register-modal').style.display = 'flex';
        document.getElementById('cancel-register').onclick = () => document.getElementById('register-modal').style.display = 'none';
        document.getElementById('confirm-register').onclick = () => {
            const name = document.getElementById('reg-name').value.trim();
            const email = document.getElementById('reg-email').value.trim();
            if (name && email) {
                userData = {name, email};
                localStorage.setItem('tokogamers_user', JSON.stringify(userData));
                updateUI();
                document.getElementById('register-modal').style.display = 'none';
            } else alert("Nama dan Email wajib diisi!");
        };

        document.getElementById('logout-btn').onclick = () => {
            if (confirm("Logout?")) {
                localStorage.removeItem('tokogamers_user');
                location.reload();
            }
        };

        // Submit Form
        document.getElementById('orderForm').addEventListener('submit', function(e) {
            e.preventDefault();
            if (!userData) return alert("Silakan register terlebih dahulu!");

            const orderId = "GALAXY-" + Math.random().toString(36).substring(2,10).toUpperCase();
            document.getElementById('hidden-order-id').value = orderId;

            emailjs.sendForm('service_u5bjqpt', 'template_tdfja1m', this)
                .then(() => {
                    document.getElementById('order-id').textContent = orderId;
                    document.getElementById('order-form').style.display = 'none';
                    document.getElementById('order-result').style.display = 'block';
                })
                .catch(err => alert("Gagal mengirim email. Cek koneksi atau template EmailJS."));
        });

        // Search
        document.getElementById('search-btn').onclick = () => {
            const term = document.getElementById('search-input').value.toLowerCase();
            document.querySelectorAll('.card').forEach(c => {
                c.style.display = c.textContent.toLowerCase().includes(term) ? 'block' : 'none';
            });
        };

        window.onload = () => {
            createStars();
            generateGames();
            updateUI();
        };
    </script>
</body>
</html>
