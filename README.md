# DevOps Project 1 - Trien khai ung dung Python Flask tren AWS EC2

Day la project thuc hanh DevOps co ban cua em.
Project su dung Python Flask de tao mot ung dung web don gian, dong goi bang Docker, trien khai tren AWS EC2 va tu dong deploy bang GitHub Actions.

## Muc tieu project

Project nay giup em thuc hanh cac kien thuc co ban cua DevOps nhu:

* Lam viec voi Linux server
* Su dung Git va GitHub de quan ly source code
* Dong goi ung dung bang Docker
* Deploy ung dung len AWS EC2
* Thiet lap CI/CD co ban bang GitHub Actions

## Cong nghe su dung

* Python Flask
* Docker
* AWS EC2
* GitHub
* GitHub Actions

## Cau truc project

* app.py
* requirements.txt
* Dockerfile
* README.md
* .github/workflows/deploy.yml

## Mo ta ung dung

Ung dung la mot website don gian viet bang Flask, dung de hien thi noi dung gioi thieu co ban tren trinh duyet.

Ung dung chay o cong 5000 ben trong container va duoc map ra cong 8080 tren may EC2.

## Cach chay local

### 1. Clone source code

git clone https://github.com/nguyenngocquyy/devopsproject1.git
cd devopsproject1

### 2. Build Docker image

docker build -t python-devops-web .

### 3. Run container

docker run -d --name python-devops-web -p 8080:5000 python-devops-web

### 4. Truy cap ung dung

Mo trinh duyet va vao:

http://localhost:8080

## Cach trien khai tren AWS EC2

### 1. Tao EC2 instance

* Tao mot may EC2 chay Linux
* Mo cac port can thiet trong Security Group:

  * 22 cho SSH
  * 8080 de truy cap web

### 2. Cai Docker va Git tren EC2

Vi du voi Amazon Linux:

sudo dnf update -y
sudo dnf install -y docker git
sudo systemctl enable docker
sudo systemctl start docker

### 3. Clone project ve EC2

git clone https://github.com/nguyenngocquyy/devopsproject1.git
cd devopsproject1

### 4. Build va chay container

sudo docker build -t python-devops-web .
sudo docker run -d --name python-devops-web --restart unless-stopped -p 8080:5000 python-devops-web

### 5. Truy cap tu trinh duyet

http://EC2_PUBLIC_IP:8080

## Tu dong deploy bang GitHub Actions

Project co su dung GitHub Actions de tu dong deploy khi co code moi duoc push len branch main.

### Quy trinh hoat dong

1. Developer push code len GitHub
2. GitHub Actions duoc kich hoat
3. Workflow SSH vao EC2
4. Pull code moi nhat
5. Build lai Docker image
6. Xoa container cu
7. Chay lai container moi

## GitHub Secrets can cau hinh

Trong repo GitHub, can tao cac secrets sau:

* EC2_HOST: Public IP cua EC2
* EC2_USER: user SSH vao EC2, vi du ec2-user
* EC2_SSH_KEY: private key dung de SSH vao EC2

## Ket qua dat duoc

* Xay dung thanh cong ung dung web don gian bang Flask
* Dong goi ung dung bang Docker
* Trien khai ung dung len AWS EC2
* Thiet lap duoc quy trinh tu dong deploy voi GitHub Actions

## Kien thuc hoc duoc

Thong qua project nay, em da thuc hanh duoc:

* Cac lenh Linux co ban
* Quan ly source code bang Git va GitHub
* Build va chay container bang Docker
* Cach deploy ung dung len AWS EC2
* Thiet lap CI/CD co ban voi GitHub Actions
* Xu ly mot so loi thuong gap khi deploy

## Huong phat trien trong tuong lai

Trong tuong lai, project co the duoc mo rong them:

* Gan domain rieng
* Cau hinh Nginx reverse proxy
* Cai dat HTTPS voi SSL
* Ket noi database
* Trien khai nhieu service bang Docker Compose
* Theo doi log va monitoring

## Tac gia

* Ho ten: Nguyen Ngoc Quy
* Muc tieu: Thuc hanh va phat trien ky nang DevOps co ban

