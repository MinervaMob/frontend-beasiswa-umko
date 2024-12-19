<script lang="ts">
    import { onMount } from "svelte";

    // Definisikan tipe untuk data beasiswa
    interface Beasiswa {
        id: number;
        beasiswaName: string;
        openDate: string;
        closeDate: string;
        description: string;
        jenjang: string;
        sumber: string;
        tujuan: string;
        target: string;
    }

    let beasiswa: Beasiswa[] = []; // Tipe data array of Beasiswa
    let loading: boolean = true; // Tipe boolean
    let error: string | null = null; // Tipe string atau null

    // Ambil data JSON dari file eksternal
    onMount(async () => {
        try {
            const response = await fetch("/data/beasiswa.json");
            if (!response.ok) {
                throw new Error(
                    "Gagal mengambil data, status: " + response.status,
                );
            }
            beasiswa = (await response.json()) as Beasiswa[]; // Casting ke tipe Beasiswa[]
        } catch (err: unknown) {
            if (err instanceof Error) {
                error = err.message; // Tipe aman
            } else {
                error = "Terjadi kesalahan yang tidak diketahui.";
            }
        } finally {
            loading = false;
        }
    });

    // Fungsi untuk mengecek status beasiswa
    const checkStatus = (openDate: string, closeDate: string): string => {
        const tanggalSekarang = new Date();
        const tanggalBuka = new Date(openDate);
        const tanggalTutup = new Date(closeDate);

        // Pastikan openDate dan closeDate memiliki format yang valid
        if (isNaN(tanggalBuka.getTime()) || isNaN(tanggalTutup.getTime())) {
            return "Invalid date format"; // Validasi jika tanggal tidak valid
        }

        if (tanggalSekarang >= tanggalBuka || tanggalSekarang <= tanggalTutup) {
            return "on-going"; // Status sedang berlangsung
        } else {
            return "closed"; // Status ditutup
        }
    };
</script>

<!-- Tampilan Data -->
<div class="section-beasiswa">
    {#if loading}
        <p class="loading">Loading data...</p>
    {:else if error}
        <p class="error">Error: {error}</p>
    {:else}
        {#each beasiswa as item}
            <div class="beasiswa-card">
                <h2 class="beasiswa-title">{item.beasiswaName}</h2>
                <div class="beasiswa-info">
                    <div class="date d-flex gap-4">
                        <p><strong>Tanggal Dibuka:</strong> {item.openDate}</p>
                        <p>
                            <strong>Tanggal Ditutup:</strong>
                            {item.closeDate}
                        </p>
                    </div>
                    <!-- Tombol Status -->
                    {#if checkStatus(item.openDate, item.closeDate) === "on-going"}
                        <div class="btn bg-success rounded-5 mt-3 text-white">
                            On-going
                        </div>
                    {:else}
                        <div class="btn bg-danger rounded-5 mt-3 text-white">
                            Closed
                        </div>
                    {/if}
                    <button type="button" class="btn bg-warning mt-3 rounded-5"
                        ><a href="/detail" class="text-decoration-none text-black">Detail</a></button
                    >
                    <p class="mt-3">{item.description}</p>
                    <div class="info-detail d-flex gap-5 mt-3">
                        <p><strong>Jenjang:</strong><br /> {item.jenjang}</p>
                        <p><strong>Sumber:</strong><br /> {item.sumber}</p>
                        <p><strong>Tujuan:</strong><br /> {item.tujuan}</p>
                        <p><strong>Target:</strong><br /> {item.target}</p>
                    </div>
                </div>
            </div>
        {/each}
    {/if}
</div>

<style>
    .beasiswa-card {
        border: 1px solid #ddd;
        border-radius: 8px;
        padding: 16px;
        margin: 8px 0;
        background-color: #f9f9f9;
    }
    .beasiswa-title {
        font-size: 1.2em;
        font-weight: bold;
        margin-bottom: 8px;
    }
    .beasiswa-info p {
        margin: 4px 0;
    }
    .loading,
    .error {
        color: red;
        font-style: italic;
    }
</style>
