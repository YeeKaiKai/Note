### 概念（v.s. Virtual Machine）
#### Container

- 在作業系統層上虛擬化
- Container 共享 OS
- 資源輕量化、啟動速度快
![[Pasted image 20250831195855.png]]
#### Virtual Machine

- 在硬體層上虛擬化
- 每個 VM 有各自 OS
- 需要較多資源、啟動速度慢
![[Pasted image 20250831195716.png]]

### 一些用過的指令

- `docker ps` : show all containers that are currently running
- `docker ps -a` : show all containers 
- `docker run -it <container> sh` : create a container, give a tty interface, and run the container interactively