---

---
---
## 基本概念

---
### Image

- Read-only file，由 Dockerfile 建立
- 一個模板，用以重複產生容器實體，裡面可以有 MySQL 服務、Node.js 編譯環境、Ubuntu 作業系統等等
### Container

- 由 image 建立出的執行 instance
### Repository

- 集中存放 images 的地方，Registry 則存放多個 Repository
### Container v.s. Virtual Machine
#### Container

- 在作業系統層上虛擬化
- Container 共享 kernel
- 資源輕量化、啟動速度快

![[Pasted image 20250831195855.png]]
#### Virtual Machine

- 在硬體層上虛擬化
- 每個 VM 有各自 OS
- 需要較多資源、啟動速度慢

![[Pasted image 20250831195716.png]]
## 指令
---
- `docker ps` : show all containers that are currently running
- `docker ps -a` : show all containers 
- `docker run -it <image> <command>` : create a container, give a tty interface, and run the container interactively--