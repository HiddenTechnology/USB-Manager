## Transferência de Arquivos via Cabo USB

Este guia explica como ativar e usar a transferência de arquivos via cabo USB no R36S, permitindo conectar o console ao PC via SFTP (WinSCP, FileZilla, etc.).

### Requisitos

- Cabo USB (o mesmo usado para carregar o console).
- PC com Windows (ou outro sistema com cliente SFTP).
- Programa de transferência: **WinSCP**, **FileZilla** ou similar.

---

### Passo 1 – Acessar o USB Manager no dArkOS re

1. No R36S, abra o **EmulationStation**.
2. Vá até **Opção**
3. Procure a pasta **Tools**
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

### Passo 3 (Windows) - Configurar a Conexão

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

### Passo 4 (Linux) - Configurar a Conexão

1. Conecte o R36S ao PC via cabo USB.
2. No Linux, abra as **Configurações de Rede** ou use o terminal.
3. O sistema deve detectar automaticamente uma nova interface de rede (geralmente `enp0s20f0u1`, `usb0`, `eth1` ou similar).
4. A interface deve receber automaticamente o IP `192.168.2.1` via DHCP.

> **Se não receber IP automático (configuração manual):**
> 1. Abra o terminal.
> 2. Execute:
>    ```bash
>    sudo ip addr add 192.168.2.1/24 dev <nome_da_interface>
>    ```
>    sudo ip link set <nome_da_interface> up
>    ```
>    (Substitua `<nome_da_interface>` pelo nome da interface USB, ex.: `usb0`, `eth1`, etc.)

---

### Passo 5 (Linux) – Conectar via SFTP

1. Abra um terminal ou use um cliente SFTP gráfico (FileZilla, Nautilus, Dolphin, etc.).
2. **Via terminal (comando sftp):**
   ```bash
sftp ark@192.168.2.2
   ```
Senha: ark

---

Via FileZilla:

  -**Host:** `192.168.2.2`
  -**Porta:** `22`
  -**Usuário:** `ark`
  -**Senha:** `ark`
  -**Protocolo:** `SFTP`
Clique em Conectar.

---

### Passo 6 – Conectar via WinSCP (ou FileZilla)

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

### Passo 7 – Transferir Arquivos

1. No WinSCP, navegue até a pasta desejada no R36S (ex.: `/roms`, `/bios`, `/saves`).
2. Arraste os arquivos entre o PC e o R36S.
3. Ao terminar, feche o WinSCP.

---

### Passo 8 – Desativar a Transferência via USB

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
---

<table>
  <tr>
    <th colspan="2" style="text-align: center;">R36S</th>
  </tr>
  <tr>
    <td align="left"><b>Sistema</b></td>
    <td align="center"><b>Status</b></td>
  </tr>
  <tr>
    <td>DarkOS Re</td>
    <td align="center">✅ Testado</td>
  </tr>
</table>
