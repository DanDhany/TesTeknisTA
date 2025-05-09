<template>
  <div id="app">
    <header>
      <h1>Halo, Para Peserta Tes 👋</h1>
      <p>Terima kasih telah berpartisipasi dalam proses seleksi <strong>Tenaga Ahli Dinas Komunikasi dan Informatika
          Provinsi Jawa Timur</strong>. Kami sangat mengapresiasi waktu dan usaha yang telah Anda berikan.</p>
    </header>

    <main class="container">
      <section>
        <p>Berikut adalah beberapa informasi penting terkait tahapan <strong>Tes Teknis</strong>:</p>

        <h2>📅 Waktu dan Durasi Tes</h2>
        <ul>
          <li>Tes akan dimulai pada <strong>Sabtu, 10 Mei 2025 pukul 08.00 s.d. 15.00 WIB (7 jam)</strong>.</li>
          <li>Pastikan Anda mempersiapkan diri dengan baik dan berada di tempat yang nyaman selama pelaksanaan tes.</li>
        </ul>

        <h2>💻 Format Tes</h2>
        <ul>
          <li>Pelaksanaan tes dilakukan secara <strong>daring</strong> di tempat masing-masing.</li>
          <li>Tes terdiri dari beberapa tugas yang dapat diakses melalui link berikut:<br /><span id="countdown">⏳
              Menunggu waktu akses...</span>
            <div id="link-container"></div>
          </li>
          <li>Silakan selesaikan seluruh tugas sesuai dengan instruksi yang disediakan.</li>
          <li>Buat dokumentasi instalasi dan petunjuk penggunaan <strong>SECARA DETAIL</strong> pada file
            <code>README.md</code>.
          </li>
          <li>Penggunaan metode deployment seperti <strong>Docker</strong> akan menjadi nilai tambah.</li>
          <li>Pastikan program berjalan lancar dan <strong>bebas dari error</strong>.</li>
        </ul>

        <h2>📤 Instruksi Pengumpulan</h2>
        <ul>
          <li>Hasil kerja dikumpulkan melalui <strong>GitHub Repository pribadi</strong>.</li>
          <li>Undang reviewer dengan permission <strong>read & clone</strong> ke akun berikut:</li>
          <ul>
            <li>ifiqhan@gmail.com</li>
            <li>martin.ivo.aptika@gmail.com</li>
            <li>rino.ramadhani@gmail.com</li>
            <li>dimas6597@gmail.com</li>
          </ul>
          <li>Waktu pengumpulan dilihat dari <strong>commit terakhir</strong> pada repository Anda.</li>
          <li>Setelah selesai, lakukan konfirmasi melalui formulir: <a href="https://s.id/SubmitTest"
              target="_blank">https://s.id/SubmitTest</a></li>
        </ul>

        <h2>🧪 Instruksi Demo Aplikasi</h2>
        <ul>
          <li>Peserta hadir langsung ke lokasi wawancara sesuai jadwal:</li>
          <li><strong>Hari/Tanggal:</strong> Rabu, 14 Mei 2025</li>
          <li><strong>Waktu:</strong> 09.00 WIB – selesai</li>
          <li><strong>Tempat:</strong> Bidang Aplikasi Informatika (Lantai 3)<br />Kantor Dinas Komunikasi dan
            Informatika Provinsi Jawa Timur<br />Jl. Ahmad Yani No. 242-244, Gayungan, Surabaya</li>
          <li>Pastikan laptop dan aplikasi Anda siap untuk demo sebelum giliran Anda tiba.</li>
          <li>Lakukan pengetesan secara mandiri sebelum sesi dimulai.</li>
        </ul>

        <h2>📞 Kontak Informasi</h2>
        <ul>
          <li><strong>Ramadhany Krismaliq Sjamdra</strong><br />Email: <a
              href="mailto:ramadhany.krsj@jatimprov.go.id">ramadhany.krsj@jatimprov.go.id</a><br />WA: +62 851-5533-6566
          </li>
          <li><strong>Dimas Ikbalul Aulia</strong><br />WA: +62 898-3498-757</li>
        </ul>

        <p>Semoga sukses dalam mengikuti tahapan seleksi ini. Salam hangat,</p>
        <p><strong>Tim Aplikasi – Bidang Aplikasi Informatika<br />Dinas Komunikasi dan Informatika Provinsi Jawa
            Timur</strong></p>
      </section>
    </main>

    <footer>
      &copy; 2025 Dinas Komunikasi dan Informatika Provinsi Jawa Timur
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

      const encryptedLink = "aHR0cHM6Ly9zLmlkL1Rlc1Rla25pc0Z1bGxzdGFjayI="; // Base64 encoded link

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
