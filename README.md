# Multiple container dalam 1 host/server/node

Implementasi beberapa container dalam 1 node dengan memanfaatkan nginx-reverse-proxy. 

Dalam contoh ini, saya sertakan 2 contoh basic app (expressjs dan laravel), yang sebenarnya bisa terpisah dari repo ini (memiliki repo masing-masing / di develop beda tim). Repo ini sebenarnya hanya untuk reverse-proxy nya. 

```
├── README.md
├── docker-compose.yml
├── expressjs
└── laravel
```

Bayangkan bahwa **expressjs** dan **laravel** merupakan container, dan akan di deploy dalam 1 node/host, dan masing-masing menggunakan subdomain. Gambarannya sebagai berikut :


<img align="left" alt="schema" src="https://drive.google.com/uc?id=1aH_QhYeeyFmT1K9Vh8NLnsrIBdduEwmX&export=download" />


## Langkah - langkah

- Pastikan docker dan docker-compose sudah terinstall di node/server
- Agar nginx-proxy dapat mengarahkan ke service mana (dari subdomain), perlu dibuatkan 1 network external dari docker : ```docker network create nginx-proxy-net```
- Di directory root, sesuaikan file .env, kemudian jalankan perintah : ```docker-compose up -d```

<img align="left" alt="schema" src="https://drive.google.com/uc?id=1_P6cUws8B4nEkU-j2EzUudfx4456oWcc&export=download" />

- Di directory expressjs, jalankan perintah : 
```
docker-compose build
docker-compose up -d
```

<img align="left" alt="schema" src="https://drive.google.com/uc?id=1wx6lNhpiN7d-ulU5xi7XWPsDFxhDCanb&export=download" />


- Di directory laravel, sesuaikan file .env, kemudian jalankan perintah :
```
docker-compose build
docker-compose up -d
```

<img align="left" alt="schema" src="https://drive.google.com/uc?id=1Zxr8sJeopeiCIfCTpY2VUctA13lA2w6D&export=download" />