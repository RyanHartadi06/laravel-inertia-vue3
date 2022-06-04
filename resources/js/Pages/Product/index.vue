<template>
    <div class="mt-5">
        <!-- flash message -->
        <!-- <div
            v-if="$page.props.flash.message"
            class="alert alert-success"
            role="alert"
        >
            {{ $page.props.flash.message }}
        </div> -->
        <!-- flash message -->
        <div class="mb-3">
            <Link href="/products/create" class="btn btn-md btn-primary"
                >TAMBAH DATA</Link
            >
        </div>
        <div class="card border-0 rounded shadow-sm">
            <div class="card-body">
                <table class="table">
                    <thead>
                        <tr>
                            <th scope="col">Nomor</th>
                            <th scope="col">Nama Produk</th>
                            <th scope="col">Harga</th>
                            <th scope="col">Image</th>
                            <th scope="col">ACTIONS</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <td>1</td>
                            <td>Kecap ABC</td>
                            <td>12000</td>
                            <td>img url</td>
                            <td class="text-center"></td>
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

export default {
    layout: LayoutApp,
    components: {
        Link,
    },
};
</script>
