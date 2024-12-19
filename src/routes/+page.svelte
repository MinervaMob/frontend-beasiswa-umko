<script>
    import Navbar from "../template/Navbar.svelte";
    import Footer from "../template/Footer.svelte";
    import Beasiswa from "../template/Beasiwa.svelte";
    import Filters from "../template/Filters.svelte";
    import Daftar from "../template/Daftar.svelte";
</script>

<svelte:head>
    <title>Beranda | my App</title>
</svelte:head>

<Navbar />

<div class="hero-section">
    <div class="tagline">
        <h1>Beasiswa Kuliah</h1>
        <p>
            Tidak perlu khawatir tentang biaya kuliah. Temukan beragam beasiswa
            yang cocok dengan potensi dirimu.
        </p>
    </div>
</div>

<!-- Content -->
<div class="container">
    <!-- Beasiswa Aktif Section -->
    <Beasiswa />

    <!-- Beasiswa Tersedia -->
    <Filters />

    <!-- Daftar Semua Beasiswa -->
    <Daftar />
</div>

<!-- Footer -->
<Footer />
