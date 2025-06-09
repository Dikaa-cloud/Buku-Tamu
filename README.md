<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Buku Tamu TKJ</title>
  <style>
    /* --- GAYA CSS MASIH SAMA --- */
    * {
      box-sizing: border-box;
    }

    body {
      margin: 0;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      background: #0a0a0a;
      color: #ff4d4d;
      overflow: hidden;
    }

    body::before {
      content: "";
      position: absolute;
      width: 200%;
      height: 200%;
      background-image: radial-gradient(#ff4d4d 1px, transparent 1px);
      background-size: 40px 40px;
      animation: gridMove 30s linear infinite;
      z-index: 0;
      opacity: 0.05;
    }

    @keyframes gridMove {
      0% { transform: translate(0, 0); }
      100% { transform: translate(-100px, -100px); }
    }

    .container {
      position: relative;
      z-index: 1;
      height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      perspective: 1000px;
    }

    .form-card {
      background: rgba(30, 0, 0, 0.3);
      padding: 40px;
      border: 2px solid #ff4d4d;
      border-radius: 15px;
      box-shadow: 0 0 30px #ff4d4d;
      width: 400px;
      transform-style: preserve-3d;
      animation: floatCard 6s ease-in-out infinite;
    }

    @keyframes floatCard {
      0%, 100% { transform: rotateY(0deg) rotateX(0deg); }
      50% { transform: rotateY(10deg) rotateX(10deg); }
    }

    .form-card h2 {
      text-align: center;
      margin-bottom: 30px;
      text-shadow: 0 0 10px #ff4d4d;
    }

    .input-group {
      margin-bottom: 20px;
    }

    .input-group label {
      display: block;
      margin-bottom: 5px;
      color: #ff9999;
    }

    .input-group input,
    .input-group select,
    .input-group textarea {
      width: 100%;
      padding: 10px;
      border: 1px solid #ff4d4d;
      border-radius: 5px;
      background-color: #1a0000;
      color: white;
      outline: none;
      transition: 0.3s;
      box-shadow: inset 0 0 10px transparent;
    }

    .input-group input:focus,
    .input-group select:focus,
    .input-group textarea:focus {
      box-shadow: inset 0 0 10px #ff4d4d;
    }

    .submit-button {
      width: 100%;
      padding: 12px;
      background-color: #ff4d4d;
      color: white;
      font-weight: bold;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      transition: 0.3s;
      box-shadow: 0 0 10px #ff4d4d;
    }

    .submit-button:hover {
      background-color: #cc0000;
      box-shadow: 0 0 20px #ff4d4d;
    }

    .success-message {
      text-align: center;
      margin-top: 20px;
      color: #00ff99;
    }
  </style>
</head>
<body>
  <div class="container">
    <div class="form-card">
      <h2>BUKU TAMU TKJ 🤗</h2>
      <form id="bukutamu-form" action="https://formsubmit.co/haloakuun@gmail.com" method="POST">
        <!-- Ganti youremail@gmail.com dengan email kamu -->
        <div class="input-group">
          <label for="nama">Nama Lengkap</label>
          <input type="text" id="nama" name="Nama Lengkap" required />
        </div>
        <div class="input-group">
          <label for="kelas">Kelas</label>
          <select id="kelas" name="Kelas" required>
            <option value="">-- Pilih Kelas --</option>
            <option value="XI TKJ">XI TKJ</option>
            <option value="XI TJA">XI TJA</option>
            <option value="XI DKV">XI DKV</option>
            <option value="XI OTKP">XI OTKP</option>
            <option value="XI RPL">XI RPL</option>
            <option value="XI ANIMASI">XI ANIMASI</option>
          </select>
        </div>
        <div class="input-group">
          <label for="keperluan">Keperluan</label>
          <textarea id="keperluan" name="Keperluan" rows="3" required></textarea>
        </div>
        <div class="input-group">
          <label for="waktu">Waktu Kunjungan</label>
          <input type="datetime-local" id="waktu" name="Waktu Kunjungan" required />
        </div>
        <button type="submit" class="submit-button">KIRIM</button>
        <p class="success-message" id="success-message" style="display: none;">
          ✅ Terima kasih! Data Anda berhasil dikirim.
        </p>
      </form>
    </div>
  </div>

  <script>
    document.getElementById('bukutamu-form').addEventListener('submit', function(e) {
      // Bisa dihapus jika ingin langsung kirim ke email
      e.preventDefault();

      // Kirim data via FormSubmit
      const form = e.target;
      const formData = new FormData(form);

      fetch(form.action, {
        method: 'POST',
        body: formData,
        headers: {
          'Accept': 'application/json'
        }
      }).then(response => {
        if (response.ok) {
          document.getElementById('success-message').style.display = 'block';
          form.reset();
        } else {
          alert('Terjadi kesalahan saat mengirim. Coba lagi.');
        }
      });
    });
  </script>
</body>
</html>