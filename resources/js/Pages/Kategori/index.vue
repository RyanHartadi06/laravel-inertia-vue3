<template>
    <div class="mt-5">
        <!-- flash message -->
        <div
            v-if="$page.props.flash.message"
            class="alert alert-success"
            role="alert"
        >
            {{ $page.props.flash.message }}
        </div>
        <!-- flash message -->
        <div class="mb-3">
            <Link href="/category/create" class="btn btn-md btn-primary"
                >TAMBAH DATA</Link
            >
        </div>
        <div class="card border-0 rounded shadow-sm">
            <div class="card-body">
                <table class="table">
                    <thead>
                        <tr>
                            <th scope="col">Nomor</th>
                            <th scope="col">Nama Kategori</th>
                            <th scope="col">Actions</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr
                            v-for="(categories, index) in category"
                            :key="categories.id"
                        >
                            <td>{{ index + 1 }}</td>
                            <td>{{ categories.name }}</td>
                            <td>
                                <Link
                                    :href="`/category/${categories.id}/edit`"
                                    class="btn btn-primary btn-md shadow-sm me-2"
                                >
                                    Edit
                                </Link>
                                <button
                                    @click.prevent="
                                        deletePost(`${categories.id}`)
                                    "
                                    class="btn btn-warning btn-md shadow-sm"
                                >
                                    Delete
                                </button>
                            </td>
                        </tr>
                    </tbody>
                </table>
            </div>
        </div>
    </div>
</template>

<script>
import LayoutApp from "../../Layouts/navbar.vue";
import { Link } from "@inertiajs/inertia-vue3";
import { Inertia } from "@inertiajs/inertia";
export default {
    layout: LayoutApp,

    components: {
        Link,
    },
    //props
    props: {
        category: Array, // <- nama props yang dibuat di controller saat parsing data
    },
    setup() {
        //method deletePost
        function deletePost(id) {
            Inertia.delete(`/category/${id}`);
        }

        return {
            deletePost,
        };
    },
};
</script>
