<template>
  <div class="judul px-15">
    <div class="font-calibri text-1l py-5">Selamat Datang di Halaman Dashboard </div>
    </div>
  <div class="dashboard py-20">
    <div class="box box-1">
      <span class="pi pi-user icon"></span>
      <div class="content font-bold">
        <h2>20</h2>
        <p>More information</p>
      </div>
    </div>
    <div class="box box-2">
      <span class="pi pi-users icon"></span>
      <div class="content font-bold">
        <h2>400</h2>
        <p>More information</p>
      </div>
    </div>
    <div class="box box-3">
      <span class="pi pi-cog icon"></span>
      <div class="content font-bold">
        <h2>Setting</h2>
        <p>More information</p>
      </div>
    </div>
    <div class="box box-4">
      <span class="pi pi-grad icon"></span>
      <div class="content font-bold">
        <h2>Pengunjung</h2>
        <p>More information</p>
      </div>
    </div>
  </div>
</template>

<style>


.judul {
  text-align: left;
  margin-bottom: 5px;
  border-bottom: 2px solid #868686;
}

.dashboard {
  display: grid;
  grid-template-columns: repeat(4, 0fr);
  grid-gap: 20px;
}

.box {
  display: flex;
  align-items: center;
  width: 250px;
  height: 100px;
  padding: 20px;
  border-radius: 0px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.icon {
  font-size: 50px;
  margin-right: 40px;
}

.content {
  text-align: right;
}

.box-1 {
  background-color: #f00505;
}

.box-2 {
  background-color: #069f09;
}

.box-3 {
  background-color: #2493dc;
}

.box-4 {
  background-color: #f9a006;
}

.icon {
  font-size: 36px;
  margin-bottom: 10px;
  color: #555555;
}

.box h2 {
  margin-bottom: 10px;
  font-size: 25px;
  color: #f9f7f7;
  
}

.box p {
  font-size: 10px;
  text-align: right ;
  color: #fdfcfc;
  margin-top: 30px;
  margin-left: 40px;
}
</style>