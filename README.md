## Cisco Packet Tracer ile Basit Bir Şirket Ağı Yapılandırma

Bu yazıda, Cisco Packet Tracer kullanarak basit bir şirket ağının nasıl oluşturulacağını ve yapılandırılacağını anlatacağım. Bu ağ, iki farklı şubeyi (Antalya ve Isparta) birbirine bağlayan ve her bir şubede statik IP adresleri ile çalışan cihazlardan oluşmaktadır.

### Ağa Genel Bakış

- **Verkosis Antalya Şubesi**
  - **Router0 (Gig0/0: 192.168.3.1, Gig0/1: 10.0.0.1)**
  - **Switch0**
  - **PC0 (192.168.3.x, statik IP)**
  - **Laptop0 (192.168.3.x, statik IP)**

- **Verkosis Isparta Şubesi**
  - **Router1 (Gig0/0: 192.168.4.1, Gig0/1: 10.0.0.2)**
  - **Switch1**
  - **PC1 (192.168.4.x, statik IP)**
  - **Laptop1 (192.168.4.x, statik IP)**

### Yapılandırma Adımları

#### 1. Router Yapılandırması

**Antalya Router (Router0):**
- GigabitEthernet0/0 arayüzünü yapılandırın:
  ```plaintext
  Router0> enable
  Router0# configure terminal
  Router0(config)# interface gig0/0
  Router0(config-if)# ip address 192.168.3.1 255.255.255.0
  Router0(config-if)# no shutdown
  ```
- GigabitEthernet0/1 arayüzünü yapılandırın:
  ```plaintext
  Router0(config)# interface gig0/1
  Router0(config-if)# ip address 10.0.0.1 255.255.255.0
  Router0(config-if)# no shutdown
  ```

**Isparta Router (Router1):**
- GigabitEthernet0/0 arayüzünü yapılandırın:
  ```plaintext
  Router1> enable
  Router1# configure terminal
  Router1(config)# interface gig0/0
  Router1(config-if)# ip address 192.168.4.1 255.255.255.0
  Router1(config-if)# no shutdown
  ```
- GigabitEthernet0/1 arayüzünü yapılandırın:
  ```plaintext
  Router1(config)# interface gig0/1
  Router1(config-if)# ip address 10.0.0.2 255.255.255.0
  Router1(config-if)# no shutdown
  ```

#### 2. Switch Yapılandırması

Switch'lerde herhangi bir özel yapılandırmaya gerek yoktur, cihazlar otomatik olarak bağlantı kurar.

#### 3. PC ve Laptop IP Adreslerinin Atanması

**Antalya Şubesi:**
- PC0 ve Laptop0 için statik IP adreslerini atayın:
  ```plaintext
  IP Adresi: 192.168.3.x
  Alt Ağ Maskesi: 255.255.255.0
  Varsayılan Ağ Geçidi: 192.168.3.1
  ```

**Isparta Şubesi:**
- PC1 ve Laptop1 için statik IP adreslerini atayın:
  ```plaintext
  IP Adresi: 192.168.4.x
  Alt Ağ Maskesi: 255.255.255.0
  Varsayılan Ağ Geçidi: 192.168.4.1
  ```

### Test ve Doğrulama

Ağınızı doğru şekilde yapılandırdıktan sonra, cihazların birbirleriyle iletişim kurabildiğinden emin olmak için ping komutunu kullanarak test yapabilirsiniz. Örneğin:

- Antalya şubesindeki bir cihazdan Isparta şubesindeki bir cihaza ping atarak bağlantıyı kontrol edin:
  ```plaintext
  ping 192.168.4.x
  ```

Eğer ping başarılı olursa, ağınız doğru şekilde yapılandırılmış demektir.

### Sonuç

Bu yazıda, Cisco Packet Tracer kullanarak basit bir şirket ağının nasıl oluşturulacağını ve yapılandırılacağını adım adım inceledik. Router, switch ve cihazların yapılandırmalarını doğru şekilde yaparak, iki farklı şubeyi başarılı bir şekilde birbirine bağladık. Bu tür bir ağ, şirketlerin şubeleri arasında güvenilir ve sürekli bir iletişim sağlar.

---
