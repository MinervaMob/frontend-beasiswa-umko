<script>
</script>

<div class="filter-beasiswa p-5 text-center">
    <h1 class="text-center fs-4">Daftar Beasiswa Tersedia</h1>
    <div class="search mt-5 d-flex">
        <input
            type="search"
            id="search"
            name="search"
            placeholder="Keyword Beasiswa"
        />
        <button type="submit" class="btn bg-warning rounded-0 shadow-lg">
            <i class="bi bi-search"></i>
        </button>
    </div>
    <div class="filter mt-4 p-3 shadow">
        <h2 class="text-start fs-4">Filters</h2>
        <div class="check-filter mt-4">
            <div class="row">
                <div class="col text-start">
                    <h6>Status</h6>
                    <input type="checkbox" name="on_going" id="on_going" />
                    <label for="on_going">On-Going</label><br>
                    <input type="checkbox" name="coming_soon" id="coming_soon" />
                    <label for="coming_soon">Coming Soon</label><br>
                    <input type="checkbox" name="closed" id="closed" />
                    <label for="on_going">Closed</label>
                </div>
                <div class="col text-start">
                    <h6>Jenjang</h6>
                    <input type="checkbox" name="vokasi" id="vokasi" />
                    <label for="vokasi">Vokasi</label><br>
                    <input type="checkbox" name="sarjana" id="sarjana" />
                    <label for="sarjana">Sarjana</label><br>
                    <input type="checkbox" name="magister" id="magister" />
                    <label for="magister">Magister</label><br>
                    <input type="checkbox" name="doktoral" id="doktoral" />
                    <label for="doktoral">Doktoral</label>
                </div>
                <div class="col text-start">
                    <h6>Sumber</h6>
                    <input type="checkbox" name="internal" id="internal" />
                    <label for="internal">Beasiswa Internal</label><br>
                    <input type="checkbox" name="external" id="external" />
                    <label for="external">Beasiswa External</label>
                </div>
                <div class="col text-start">
                    <h6>Tujuan</h6>
                    <input type="checkbox" name="umko" id="umko" />
                    <label for="umko">UMKO</label><br>
                    <input type="checkbox" name="ex-umko" id="ex-umko" />
                    <label for="ex-umko">Universitas di luar UMKO</label>
                </div>
            </div>
            <div class="row mt-4">
                <div class="col text-start">
                    <h6>Target</h6>
                    <input type="checkbox" name="new_student" id="new_student" />
                    <label for="new_student">Mahasiswa Baru</label><br>
                    <input type="checkbox" name="active_student" id="active_student" />
                    <label for="active_student">Mahasiswa Aktif</label><br>
                </div>
            </div>
        </div>

        <div class="btn-filter text-end">
            <a href="/" class="clear-filters text-decoration-none me-3 fw-semibold">Clear Filter</a>
            <a href="/" class="filter btn fw-semibold">Filter</a>
        </div>
    </div>
</div>
