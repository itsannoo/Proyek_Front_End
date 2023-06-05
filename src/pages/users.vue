<template>
    <div class="px-15">
      <div class="font-bold text-4xl py-10">Data Siswa</div>
      <div class="py-15">
        <table class="border-collapse border-2 w-full">
          <thead>
            <tr>
              <th class="border-2 p-3">NISN</th>
              <th class="border-2 p-3">Nama</th>
              <th class="border-2 p-3">Tanggal Lahir</th>
              <th class="border-2 p-3">Kelas</th>
              <th class="border-2 p-3">Action</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="data in posts" :key="data.id">
              <td class="border-2 p-3">{{ data.id }}</td>
              <td class="border-2 p-3">{{ data.description }}</td>
              <td class="border-2 p-3">{{ data.date }}</td>
              <td class="border-2 p-3">{{ data.number }}</td>
              <td class="border-2 p-3">{{ data.text }}
                <!-- <button class="px-4 py-2 border rounded bg-blue-500 text-white hover:bg-blue-400" @click="edit(data.id)">Edit</button> -->
                <button class="px-4 py-2 border rounded bg-blue-500 text-white hover:bg-blue-400" @click="edit(data.id)">Edit</button>
                <button class="px-4 py-2 border rounded bg-red-500 text-white hover:bg-red-400" @click="destory(data.id)">Delete</button>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
      <div class="flex justify-center items-center space-x-8 py-10">
        <button class="px-4 py-2 border rounded bg-gray-500 text-white hover:bg-gray-400" @click="modelAdd = true">Tambah Data</button>
      </div>
      <!-- Pop up modal add new -->
      <div class="flex w-full h-full justify-center item-center" v-show="modelAdd">
        <!-- Background -->
        <div class="w-screen h-full bg-gray-900 bg-opacity-80 top-0 fixed sticky-0 left-0" @click="(modelAdd = false)"></div>
        <!-- Form -->
        <div class="flex justify-center items-center top-[30%] fixed sticky-0 left-[40%]">
          <div class="md:w-auto relative flex flex-col justify-center items-center bg-white p-8">
            <div class="my-5">
              <h1 role="main" class="text-xl font-semibold text-center text-gray-800">Tambah Data</h1>
            </div>
            <div class="mt-2 flex flex-col space-y-2">
              <input type="text" class="py-2 px-1 border-2 w-full text-gray-800 text-base leading-4 text-left mt-2 focus:outline-2" placeholder="Nama" v-model="data.description">
              <input type="date" class="py-2 px-1 border-2 w-full text-gray-800 text-base leading-4 text-left mt-2 focus:outline-2" v-model="data.date">
              <input type="text" class="border-2 py-2 px-1 border-2 w-full text-gray-800 text-base leading-4 text-left mt-2 focus:outline-2" rows="8" cols="8" placeholder="Kelas" v-model="data.number">
            </div>
            <button class="mt-2 px-4 py-2 border rounded bg-gray-500 text-white hover:bg-gray-400" @click="addnew">Create</button>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  import { mapGetters } from 'vuex';
  
  export default {
    data() {
      return {
        selectedFile: null,
        modelAdd: false,
        modelUpdate: false,
        data: {
          id: '',
          name: '',
          date: '',
          description: ''
        }
      };
    },
    computed: {
      ...mapGetters({
        posts: 'post/posts'
      })
    },
    methods: {
      handleFileUpload(event) {
        this.selectedFile = event.target.files[0];
      },
      uploadImage() {
        const formData = new FormData();
        formData.append('image', this.selectedFile);
  
        axios
          .post('http://localhost:3001/api/upload', formData)
          .then(response => {
            console.log(response.data);
            console.log(response.data.imageUrl);
            // Handle the response as needed
          })
          .catch(error => {
            console.error(error);
            // Handle the error as needed
          });
      },
      addnew() {
        this.$store.dispatch('post/ADD_NEW', this.data).then(response => {
          if (response) {
            this.modelAdd = false;
            console.log('Data Berhasil Disimpan');
            console.log(this.data);
            // reset data
            this.data = {
              id: '',
              name: '',
              date: '',
              description: ''
            };
          }
        });
      },
      edit(id) {
        this.modelUpdate = true;
        this.$store.dispatch('post/GET_POST', id).then(response => {
          //set data model
          this.data.id = response[0].id;
          this.data.name = response[0].name;
          this.data.date = response[0].date;
          this.data.description = response[0].description;
        });
      },
      destory(id) {
        this.$store.dispatch('post/DELETE_POST', id).then(response => {
          if (response) {
            alert('Data ini akan di hapus');
          }
        });
      }
    }
  };
  </script>
  <style>
    /* Mengubah latar belakang menjadi gradasi warna */
    body {
      background: white
    }
  
    /* Mengubah warna teks pada tombol "Tambah Data" */
    .px-4.py-2.border.rounded.bg-gray-500.text-white.hover:bg-gray-400 {
      color: white;
    }
  </style>
  
  
  