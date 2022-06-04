<template>
    <div>
        <div class="card border-0 rounded shadow">
            <div class="card-body">
                <h4>Edit Kategori</h4>
                <hr />
                <form @submit.prevent="updateCategory">
                    <div class="mb-3">
                        <label class="form-label">Nama Kategori</label>
                        <input
                            type="text"
                            class="form-control"
                            placeholder="Masukkan Nama Kategori"
                            v-model="category.name"
                        />
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
        category: Object,
        errors: Object,
    },
    setup(props) {
        const category = reactive({
            name: props.category.name,
        });
        function updateCategory() {
            let name = category.name;
            Inertia.put(`/category/${props.category.id}`, {
                name: name,
            });
        }
        return {
            category,
            updateCategory,
        };
    },
};
</script>
