<template>
    <div>
        <div class="card border-0 rounded shadow">
            <div class="card-body">
                <h4>Tambah Produk</h4>
                <hr />
                <form @submit.prevent="submit">
                    <div class="mb-3">
                        <label class="form-label">Nama Produk</label>
                        <input
                            type="text"
                            class="form-control"
                            placeholder="Masukkan Nama Produk"
                            v-model="form.name_products"
                        />
                    </div>
                    <div class="mb-3">
                        <label class="form-label">Harga</label>
                        <input
                            type="text"
                            class="form-control"
                            placeholder="Masukkan Harga"
                            v-model="form.price"
                        />
                    </div>
                    <div class="mb-3">
                        <label class="form-label">Kategori Product</label>
                        <select
                            class="form-select"
                            aria-label="Default select example"
                            v-model="form.category_id"
                        >
                            <option
                                v-for="categories in category"
                                :key="categories.id"
                                :value="categories.id"
                            >
                                {{ categories.name }}
                            </option>
                        </select>
                    </div>
                    <div class="mb-3">
                        <label class="form-label">Image</label>
                        <input
                            type="file"
                            class="form-control"
                            placeholder="Masukkan Image"
                            @change="previewImage"
                            ref="photo"
                            name="photo"
                        />
                        <img v-if="url" :src="url" class="w-full mt-4 h-80" />
                        <div v-if="errors.image" class="font-bold text-red-600">
                            {{ errors.image }}
                        </div>
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
import { reactive } from "vue";
import { Inertia } from "@inertiajs/inertia";
import { useForm } from "@inertiajs/inertia-vue3";
export default {
    layout: LayoutApp,
    props: {
        category: Array,
        errors: Object,
    },
    data() {
        return {
            url: null,
        };
    },
    setup() {
        const form = useForm({
            image: null,
            name_products: "",
            price: "",
            category_id: "",
        });
        return { form };
    },
    methods: {
        previewImage(e) {
            const file = e.target.files[0];
            this.url = URL.createObjectURL(file);
        },
        submit() {
            this.form.image = this.$refs.photo.files[0];

            const data = {
                image: this.form.image,
                name_products: this.form.name_products,
                price: this.form.price,
                category_id: this.form.category_id,
            };
            console.log(data);
            Inertia.post("/products/", data);
        },
    },
};
</script>
