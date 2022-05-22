## Yêu cầu triển khai ứng dụng NodeJS + MongoDB

### Yêu cầu 1: Viết Dockerfile

Dockerfile chạy trên base image **node:12-alpine**

Build ra 1 Docker Image có tên là **demo-service**

### Yêu cầu 2: Viết file docker-compose.yml

File docker-compose.yml gồm 2 service có tên là **mongodb** và **nodejs**

Cấu hình service mongodb:

- Sử dụng image **mongo:latest**
- Mount volume thư mục **/data/db** ra 1 thư mục bên ngoài host

Cấu hình service nodejs:

- Chạy sau service mongodb
- Sử dụng Docker Image **demo-service** vừa build ở yêu cầu 1
- Expose cổng 3000 của ứng dụng ra cổng 8000 của ngoài host
- Định nghĩa 2 biến môi trường: MONGODB_URI=mongodb://mongodb:27017/demo, PORT=3000

## Solution:

- Viết file docker-compose.
- Tạo lables:
  docker node update <node_name> --label-add key=value
- Google tìm các cấu hình tương ứng khi viết file docker compose
- S/d docker stack deploy để deploy trên swarm.

## Troubleshooting

- Lỗi docker treo: khi mở port cho container bên trong ra ngoài ok rồi, trên node chạy container curl ok nhưng bên ngoài không kết nối dc => reboot node.
- Lỗi không tạo được mongodb khi chạy docker stack deploy nhưng chạy docker-compose up thì được:
  Error: `mkdir /var/lib/docker: read-only file system`
  Solution:
  `update cac node ve DRAIN
  snap remove docker
  rm -R /var/lib/docker
  sudo apt-get remove docker docker-engine docker.io
  install official docker: https://docs.docker.com/install/linux/docker-ce/ubuntu/`
- Các lệnh debug:
  docker stack ps --no-trunc `<stackid>`
- docker service ps `<serviceis>`
