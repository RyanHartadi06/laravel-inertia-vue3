<template>
    <div>
        <div class="card border-0 rounded shadow">
            <div class="card-body">
                <h4>Tambah Kategori</h4>
                <hr />
                <form @submit.prevent="storedata">
                    <div class="mb-3">
                        <label class="form-label">Nama Kategori</label>
                        <input
                            type="text"
                            class="form-control"
                            placeholder="Masukkan Nama Kategori"
                            v-model="post.name"
                        />
                        <div v-if="errors.name" class="mt-2 alert alert-danger">
                            {{ errors.name }}
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

export default {
    layout: LayoutApp,
    props: {
        errors: Object,
    },
    setup() {
        const post = reactive({
            name: "",
        });

        function storedata() {
            let name = post.name;

            Inertia.post("/category/", {
                name: name,
            });
        }
        return {
            post,
            storedata,
        };
    },
};
</script>
