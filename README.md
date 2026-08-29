## Transferência de Arquivos via Cabo USB – dArkOS re (R36S)

Este guia explica como ativar e usar a transferência de arquivos via cabo USB no **dArkOS re** para R36S, permitindo conectar o console ao PC via SFTP (WinSCP, FileZilla, etc.).

### Requisitos

- R36S com **dArkOS re** instalado.
- Cabo USB (o mesmo usado para carregar o console).
- PC com Windows (ou outro sistema com cliente SFTP).
- Programa de transferência: **WinSCP**, **FileZilla** ou similar.

---

### Passo 1 – Acessar o USB Manager no dArkOS re

1. No R36S, abra o **EmulationStation**.
2. Vá até **Network Settings** (ou **Configurações de Rede**).
3. Procure a opção **USB Manager** (ou **USB Transfer**).
4. Execute a script do **USB Manager**.

---

### Passo 2 – Ativar a Transferência via USB

No menu do **USB Manager**:

1. Selecione a opção:  
   **1 – Ativar transferencia**
2. Aguarde a mensagem:  
   `Transferencia ativada`
3. O menu mostrará:
   - **IP do R36S:** `192.168.2.2`
   - **IP do PC:** `192.168.2.1`

> **Nota:** A tela pode piscar durante a ativação. Isso é normal.

---

### Passo 3 – Configurar a Conexão no PC (Windows)

1. Conecte o R36S ao PC via cabo USB.
2. No Windows, abra **Conexões de Rede**:
   - Pressione `Win + R`, digite `ncpa.cpl` e dê Enter.
3. Você verá uma nova conexão de rede (geralmente chamada **Ethernet 2**, **RNDIS** ou similar).
4. Essa conexão deve receber automaticamente o IP `192.168.2.1`.

> **Se não receber IP automático:**
> 1. Clique com o botão direito na conexão → **Propriedades**.
> 2. Selecione **Protocolo IP Versão 4 (TCP/IPv4)** → **Propriedades**.
> 3. Marque **Usar o seguinte endereço IP**:
>    - **Endereço IP:** `192.168.2.1`
>    - **Máscara de sub-rede:** `255.255.255.0`
>    - **Gateway padrão:** `192.168.2.2`
> 4. Clique em **OK**.

---

### Passo 4 – Conectar via WinSCP (ou FileZilla)

1. Abra o **WinSCP** (ou outro cliente SFTP).
2. Crie uma nova conexão com os seguintes dados:
   - **Host:** `192.168.2.2`
   - **Porta:** `22`
   - **Usuário:** `ark`
   - **Senha:** `ark`
   - **Protocolo:** `SFTP`
3. Clique em **Conectar** (ou **Login**).
4. Se aparecer um aviso de chave do host, clique em **Aceitar** ou **Sim**.

---

### Passo 5 – Transferir Arquivos

1. No WinSCP, navegue até a pasta desejada no R36S (ex.: `/roms`, `/bios`, `/saves`).
2. Arraste os arquivos entre o PC e o R36S.
3. Ao terminar, feche o WinSCP.

---

### Passo 6 – Desativar a Transferência via USB

No **USB Manager** do R36S:

1. Selecione a opção:  
   **2 – Desativar transferencia**
2. Aguarde a mensagem:  
   `Transferencia desativada`
3. Você pode desconectar o cabo USB do PC.

---

### Solução de Problemas

**O WinSCP não conecta:**

- Verifique se o status no **USB Manager** mostra **Transferencia ativa**.
- No PC, abra o terminal (cmd) e teste:
  ```bash
  ping 192.168.2.2
