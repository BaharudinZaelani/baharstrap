<template>
    <div class="card mt-5">
        <div class="card-header">
            <div style="text-align: left;">Halo Bahar INI</div>
        </div>
        <div class="card-body text-center">
            <h1 class="display-6">Welcome to My Blog BaharStrap</h1>
            <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Facilis similique in fugit voluptatum, et enim omnis consequatur non soluta assumenda provident voluptates deleniti.</p>
        </div>
        <div class="card-footer">
            <div class="text-left">Copyright r diatas kecil, 2021</div>
        </div>
    </div>
    <div class="row mt-5">
        <div class="col-md">
            <div class="card">
                <div class="card-header">
                    Ruang Buku
                </div>
                <div>
                    <div class="list-group">
                        <a @click="detail(item.id)" v-for="item in books" :key="item.id" class="list-group-item list-group-item-action">
                            <div class="d-flex w-100 justify-content-between">
                            <h5 class="mb-1">{{ item.judul_buku }}</h5>
                            <small class="text-muted">{{ item.created_at.substr(0, 10) }}</small>
                            </div>
                            <p class="mb-1">{{ item.lower }}</p>
                            <small class="text-muted">{{ item.penerbit }}</small>
                        </a>
                    </div>
                </div>
            </div>
        </div>
        <!-- Entah apa yang ada di kodeku hingga blank :c -->
        <!-- <div class="col-md-6" v-if="cek">
            <div class="card">
                <div class="card-header">
                    {{ tempBooks[0].judul_buku }}
                </div>
                <div class="card-body">
                    <table class="table">
                        <tr>
                            <th>Penulis</th>
                            <td>: {{ tempBooks[0].penulis }}</td>
                        </tr>
                        <tr>
                            <th>Penerbit</th>
                            <td>: {{ tempBooks[0].penerbit }}</td>
                        </tr>
                        <tr>
                            <th>Diupload</th>
                            <td>: {{ tempBooks[0].created_at }}</td>
                        </tr>
                        <tr>
                            <th>Diupdate</th>
                            <td>: {{ tempBooks[0].updated_at }}</td>
                        </tr>
                    </table>
                </div>
            </div>
        </div> -->
        <div class="col-md-8" v-if="showTemp">
            <div class="card">
                <div class="card-header">
                    {{ tempBook[0].id }}
                </div>
                <div class="card-body">
                    <table class="table">
                        <thead>
                            <tr>
                                <th>Judul Buku</th>
                                <th>Nama Penuli</th>
                                <th>Penerbit</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr>
                                <th>{{ tempBook[0].judul_buku }}</th>
                                <td>{{ tempBook[0].penulis }}</td>
                                <td>{{ tempBook[0].penerbit }}</td>
                            </tr>
                        </tbody>
                    </table>
                </div>
            </div>
        </div>
    </div>
    {{ showTemp }}
    <div class="m-5"></div>
</template>
<script>
export default {
    name: 'Welcome',
    data() {
        return {
            books: [],
            tempBook: [],
            showTemp: false
        }
    },
    created() {
        // console.log(this.zaw)
    },
    mounted() {
        const axios = require('axios')
        axios.get('http://127.0.0.1:8000/api/book?token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1c2VybmFtZSI6IlRoZVphd3ciLCJyb2xlIjoidXNlciIsImV4cGlyZWQiOjR9.WHw01kHE6ttgEx_nI1aH9_4Ohq0OhzRY-xV9k1WYc4g')
        .then(respon => {
            this.books = respon.data.data
        })
    },
    methods: {
        detail(id){
            this.tempBook = this.books.filter((book) => {
                // console.log(book.id == id)
                return (book.id == id)
            })
            this.showTemp = true
        }
    }
}
</script>