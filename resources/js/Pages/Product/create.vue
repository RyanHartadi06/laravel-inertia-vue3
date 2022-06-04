<template>
    <div>
        <div class="card border-0 rounded shadow">
            <div class="card-body">
                <h4>Tambah Produk</h4>
                <hr />
                <form>
                    <div class="mb-3">
                        <label class="form-label">Nama Produk</label>
                        <input
                            type="text"
                            class="form-control"
                            placeholder="Masukkan Nama Produk"
                        />
                    </div>
                    <div class="mb-3">
                        <label class="form-label">Harga</label>
                        <input
                            type="text"
                            class="form-control"
                            placeholder="Masukkan Harga"
                        />
                    </div>
                    <div class="mb-3">
                        <label class="form-label">Kategori Product</label>
                        <select
                            class="form-select"
                            aria-label="Default select example"
                        >
                            <option selected>Open this select menu</option>
                            <option value="1">One</option>
                            <option value="2">Two</option>
                            <option value="3">Three</option>
                        </select>
                    </div>
                    <div class="mb-3">
                        <label class="form-label">Image</label>
                        <input
                            type="file"
                            class="form-control"
                            placeholder="Masukkan Image"
                        />
                    </div>
                    <div class="mb-3">
                        <label class="form-label">Deskripsi</label>
                        <textarea
                            class="form-control"
                            rows="5"
                            placeholder="Masukkan Deskripsi"
                        ></textarea>
                    </div>
                    <div class="mb-3">
                        <button
                            type="submit"
                            class="btn btn-primary btn-md shadow-sm me-2"
                        >
                            SIMPAN
                        </button>
                        <button
                            type="reset"
                            class="btn btn-warning btn-md shadow-sm"
                        >
                            RESET
                        </button>
                    </div>
                </form>
            </div>
        </div>
    </div>
</template>

<script>
import LayoutApp from "../../Layouts/navbar.vue";
export default {
    layout: LayoutApp,
};
</script>
