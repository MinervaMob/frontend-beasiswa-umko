<script>
    import "../css/app.css";
    import logoUmkoBeasiswa from "../image/PMB-Dashboard-Putih-Min.png";
    import { onMount } from "svelte";

    // Input Search
    // State untuk menampilkan atau menyembunyikan input search
    let showSearch = false;
    let query = "";

    // Fungsi untuk menangani pencarian
    const searchNews = () => {
        if (query.trim()) {
            console.log("Searching for:", query);
            // Tambahkan logika pencarian berita di sini
        }
    };

    // Fungsi untuk toggle input search
    const toggleSearch = () => {
        showSearch = !showSearch;
        if (showSearch) {
            onMount(() => {
                document.querySelector("#searchInput").focus();
            });
        }
    };
</script>

<nav class="navbar-section sticky-top">
    <div class="container py-2">
        <div class="header-navbar d-flex gap-3">
            <a
                href="https://www.umko.ac.id/"
                target="_blank"
                class="ms-auto text-decoration-none"
            >
                <h2 class="fs-6 fw-normal">
                    <i class="bi bi-book-half"></i>
                    MyUmko
                </h2>
            </a>

            <a
                href="https://siakad.umko.ac.id/"
                target="_blank"
                class="text-decoration-none"
            >
                <h2 class="fs-6 fw-normal">
                    <i class="bi bi-star-fill"></i>MyAkademik
                </h2>
            </a>
        </div>
        <hr class="text-white w-100" />
        <div
            class="main-navbar d-flex justify-content-center align-items-center gap-4"
        >
            <div class="brand">
                <img
                    src={logoUmkoBeasiswa}
                    alt="Logo Beasiswa Umko"
                    class="w-50"
                />
            </div>
            <div
                class="menu  h-100 w-100 d-flex justify-content-center align-items-center align-content-center"
            >
                <ul class="d-flex list-unstyled gap-4">
                    <li><a href="/">Beranda</a></li>
                    <li><a href="/">Riset</a></li>
                    <li><a href="/">Tentang UMKO</a></li>
                    <li><a href="/">Kehidupan Kampus</a></li>
                    <li><a href="/">Jejaring</a></li>
                </ul>
            </div>
            <div class="search">
                <i class="bi bi-search" on:click={toggleSearch}></i>
                <!-- Input Search -->
                {#if showSearch}
                    <input
                        id="searchInput"
                        type="text"
                        placeholder="Cari berita..."
                        bind:value={query}
                        on:keydown={(e) => e.key === "Enter" && searchNews()}
                    />
                {/if}
            </div>
        </div>
    </div>
</nav>
