# Pre-Test Bootcamp fullstack developer

## Task 1 (Virtualization)

-   Buatlah sebuah VM dengan kententuan
    -   username: `<github_user>` contoh `dimasm93`
    -   hostname: `<email_without_at>` contoh `dimas.tabeldata.com`
    -   OS: `ubuntu-20.04` atau `centos-7`
-   Install webserver `nginx`
    -   Configurasi reverse-proxy ke alamat `https://jsonplaceholder.typicode.com/todos/1` dengan url `/todo`
    -   Lakukan curl ke alamat tersebut contoh `<ip-vm-host>:<ip-vm-port-nginx>/todo` (kirimkan hasil screenshotnya simpan dalam folder `screenshot` dengan nama `task1.png`)

## Task 2 (Container)

Jika saya memiliki architecture seperti berikut:

![container-apps](docs/images/01-container.png)

Dimana berikut adalah configurasi docker image:

1. Backend container

-   image: `dimmaryanto93/udemy-springboot-app:latest`
-   port: `8080`
-   env:
    -   `DATABASE_HOST`: `<ip-domain-db>`
    -   `DATABASE_PORT`: `5432`
    -   `DATABASE_NAME`: `<db-name>`
    -   `DATABASE_PASSWORD`: `<db-password>`
        need:
    -   Database PostgreSQL v14.2

2. Frontend container

-   image: `dimmaryanto93/udemy-angular-app:latest`
-   port: `80`
-   env:
    -   `APPLICATION_PORT`: `14.15-alpine`
    -   `NGINX_ROOT_DOCUMENT`: `/var/www/html`
    -   `BACKEND_HOST`: `<ip-backend-apps>`
    -   `BACKEND_PORT`: `<port-backend-apps>`
    -   `BACKEND_CONTEXT_PATH`: `/`
-   need:
    -   Backend container

Silahkan buat docker-compose filenya, kemudian simpan dalam folder `tasks` dengan nama `docker-compose.yaml`

## Task 3 (Orchestration Container System)

1. Apa yang anda ketahui tentang Orchestration Container System?
2. Kenapa Orchestration Container System seperti Kubernetes sangat popular (menurut anda)?

Cara pengerjaan, silahkan update file ini tulis jawabanya di bawah ini

1. Orchestration Container System adalah suatu aplikasi yang dipergunakan untuk mengatur lifecycle container-container yang ada di dalam environment yang dinamik, contoh Orchestration Container System adalah kubernetes dan docker swarm. Interaksi antar kontainer dalam Orchestration container system dijalankan dengan menggunakan service dari third party, sehingga service tersebut dapat mengatur image file dalam kontainer. Orchestration bisa digunakan untuk: pembuatan dan deploy dari kontainer yang ada, redundancy dari kontainer yang ada, mengatur load setiap docker, dll.

2. Di era yang modern banyak aplikasi yang makin besar karna perubahan tren monolith ke microservice, seiring berjalannya waktu tren microservice diubah menjadi lebih mudah dikembangkan oleh tim, dan lebih cepat dikembangan, semua microservice ini ditaruh di dalam container, akibatnya jumlah container menjadi lebih banyak yang harus dijalankan dan dimanage oleh banyak server, manage container yang banyak harus menggunakan cara yang benar, dengan kata lain Orchestration hadir untuk membantu Devops untuk mengelola container dalam jumlah banyak.
