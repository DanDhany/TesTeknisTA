<template>
  <div id="app">
    <header>
      <h1>Halo, Para Peserta Test 👋</h1>
      <p>Terima kasih atas partisipasi Anda dalam proses seleksi Tenaga Ahli Kominfo Jatim.</p>
    </header>

    <div class="container">
      <p>Berikut adalah informasi penting terkait tahapan <strong>Tes Teknis:</strong></p>

      <div id="countdown">⏳ Menghitung waktu menuju tes...</div>
      <div id="link-container"></div>

      <p class="section-title">📅 Waktu dan Durasi Tes</p>
      <ul>
        <li>Tes dimulai: <strong>Sabtu, 10 Mei 2025 pukul 08.00 s.d. 15.00 WIB</strong> (7 Jam)</li>
        <li>Pastikan Anda berada di tempat yang nyaman dan siap sebelum tes dimulai</li>
      </ul>

      <p class="section-title">💻 Format Tes</p>
      <ul>
        <li>Pelaksanaan tes <strong>secara daring</strong> di tempat masing-masing</li>
        <li>Soal dapat diakses melalui link (akan muncul otomatis saat waktu tiba)</li>
        <li>Selesaikan seluruh tugas sesuai instruksi</li>
        <li>Buat dokumentasi instalasi dan petunjuk di <code>README.md</code></li>
        <li>Gunakan metode deployment seperti <strong>Docker</strong> untuk nilai lebih</li>
        <li>Pastikan program bebas dari error</li>
      </ul>

      <p class="section-title">📤 Instruksi Pengumpulan</p>
      <ul>
        <li>Kumpulkan melalui <strong>GitHub Repository pribadi</strong></li>
        <li>Undang reviewer dengan permission read & clone:</li>
        <ul>
          <li>ifiqhan@gmail.com</li>
          <li>martin.ivo.aptika@gmail.com</li>
          <li>rino.ramadhani@gmail.com</li>
          <li>dimas6597@gmail.com</li>
        </ul>
        <li>Waktu pengumpulan dinilai dari <strong>commit terakhir</strong></li>
        <li>Konfirmasi melalui form ini: <a href="https://s.id/SubmitTest" target="_blank">https://s.id/SubmitTest</a>
        </li>
      </ul>

      <p class="section-title">🧪 Instruksi Demo Aplikasi</p>
      <ul>
        <li><strong>Rabu, 14 Mei 2025, pukul 09.00 WIB</strong></li>
        <li>Tempat: <em>Kantor Dinas Kominfo Jatim, Lantai 3</em></li>
        <li>Pastikan laptop dan aplikasi siap demo</li>
        <li>Lakukan pengetesan sebelum giliran</li>
      </ul>

      <p class="section-title">📞 Kontak</p>
      <ul>
        <li>Ramadhany Krismaliq Sjamdra – <a
            href="mailto:ramadhany.krsj@jatimprov.go.id">ramadhany.krsj@jatimprov.go.id</a> / WA: +62 851-5533-6566</li>
        <li>Dimas Ikbalul Aulia – WA: +62 898-3498-757</li>
      </ul>
    </div>

    <footer>
      &copy; 2025 Tim Aplikasi • Dinas Komunikasi dan Informatika Provinsi Jawa Timur
    </footer>
  </div>
</template>

<script>
export default {
  name: "App",
  mounted() {
    this.checkTime();
    this.preventDevTools();
  },
  methods: {
    checkTime() {
      const unlockTime = new Date("2025-05-10T01:00:00Z").getTime(); // UTC+7 = 08.00 WIB
      const countdown = document.getElementById("countdown");
      const linkContainer = document.getElementById("link-container");

      const encryptedLink = "aHR0cHM6Ly9zLmlkL1Rlc1Rla25pc0Z1bGxzdGFjaw==";

      const updateCountdown = () => {
        const now = new Date().getTime();
        if (now >= unlockTime) {
          countdown.innerHTML = "✅ Soal sudah tersedia.";
          linkContainer.innerHTML = `
            <a href="${atob(encryptedLink)}" target="_blank">📝 Akses Soal Tes Sekarang</a>
          `;
        } else {
          const diff = unlockTime - now;
          const hours = Math.floor((diff / (1000 * 60 * 60)) % 24);
          const minutes = Math.floor((diff / (1000 * 60)) % 60);
          const seconds = Math.floor((diff / 1000) % 60);
          countdown.innerHTML = `⏳ Soal tersedia dalam: ${hours} jam ${minutes} menit ${seconds} detik`;
          setTimeout(updateCountdown, 1000);
        }
      };
      updateCountdown();
    },
    preventDevTools() {
      // Disable Right Click
      document.addEventListener("contextmenu", (e) => {
        e.preventDefault();
      });

      // Disable DevTools Shortcuts
      document.onkeydown = function (e) {
        if (
          e.keyCode === 123 || // F12
          (e.ctrlKey && e.shiftKey && (e.keyCode === 73 || e.keyCode === 74)) || // Ctrl+Shift+I/J
          (e.ctrlKey && e.keyCode === 85) // Ctrl+U
        ) {
          return false;
        }
      };
    }
  }
};
</script>

<style scoped>
body {
  font-family: 'Inter', sans-serif;
  margin: 0;
  background: #f4f6f8;
  color: #333;
  line-height: 1.6;
  padding: 0 20px;
}


header {
  background-color: #1e88e5;
  color: white;
  padding: 30px 20px;
  text-align: center;
}

h1 {
  margin-bottom: 10px;
}

.container {
  max-width: 800px;
  margin: 30px auto;
  background: white;
  padding: 30px;
  border-radius: 12px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
}

.section-title {
  margin-top: 30px;
  color: #1e88e5;
  font-size: 1.2em;
}

#countdown {
  background-color: #f0f8ff;
  padding: 15px;
  border-left: 5px solid #1e88e5;
  margin: 20px 0;
  font-size: 1.2em;
  font-weight: bold;
}

#link-container a {
  display: inline-block;
  margin-top: 15px;
  background-color: #2ecc71;
  color: white;
  text-decoration: none;
  padding: 12px 20px;
  border-radius: 8px;
  font-weight: bold;
  transition: 0.3s ease;
}

#link-container a:hover {
  background-color: #27ae60;
}

footer {
  text-align: center;
  font-size: 0.9em;
  color: #888;
  margin-top: 40px;
  padding-bottom: 20px;
}
</style>
