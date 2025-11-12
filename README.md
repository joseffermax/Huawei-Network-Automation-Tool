<h1 align="center">🤖 Huawei Network Automation Tool ⚙️</h1>

<p align="center">
  <img src="https://readme-typing-svg.herokuapp.com?font=Orbitron&size=28&duration=3500&pause=800&color=9046FF&center=true&vCenter=true&width=850&lines=Automação+de+Redes+Huawei;NETCONF+%7C+SSH+%7C+Python;Gerencie+e+Monitore+com+Eficiência!" alt="Título Animado">
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Status-Concluído-brightgreen.svg" alt="Status do Projeto">
  <img src="https://img.shields.io/badge/Python-3.10%2B-blue.svg" alt="Python">
  <img src="https://img.shields.io/badge/Interface-Tkinter-yellow.svg" alt="Tkinter UI">
  <img src="https://img.shields.io/badge/Protocolos-NETCONF%20%7C%20SSH-orange.svg" alt="Protocolos">
  <img src="https://img.shields.io/badge/Ambiente-Testado%20no%20eNSP-lightgrey.svg" alt="Ambiente Testado">
  <a href="https://opensource.org/licenses/MIT">
    <img src="https://img.shields.io/badge/Licença-MIT-blue.svg" alt="Licença MIT">
  </a>
</p>

<p align="center">
  Ferramenta desenvolvida em <strong>Python</strong> para automação e gerenciamento remoto de dispositivos de rede 
  <strong>Huawei</strong>, utilizando os protocolos <strong>NETCONF</strong> e <strong>SSH</strong>.  
  Projeto final do curso de <strong>Tecnologia em Telemática</strong> — <em>IFPB Campus Campina Grande</em>.
</p>

<p align="center">
  <strong>💻 Automatize, gerencie e monitore suas redes Huawei com segurança e eficiência!</strong>
</p>

---

## ☕ Execução do Script em Jupyter Notebook

O script principal foi desenvolvido em **Jupyter Notebook** para permitir uma execução modular e interativa.  
A interface foi estruturada para **testes, automações e depuração em tempo real**, mantendo clareza e praticidade.

### ▶️ Como Executar

1. Instale o **Python 3.10+** e o **Jupyter Notebook**:
   ```bash
   pip install jupyterlab notebook
   ```

2. Instale as dependências do projeto:
   ```bash
   pip install -r requirements.txt
   ```

3. Execute o notebook:
   ```bash
   jupyter notebook "Huawei Network Automation Tool - Script.ipynb"
   ```

> 💡 Recomenda-se o uso do **JupyterLab** para melhor visualização e controle do ambiente de execução.  
> O script foi testado no **Windows 10**, com suporte a **CustomTkinter**.

---
---

## 🌐 O que é o eNSP Huawei

O **eNSP (Emulator Network Simulation Platform)** é o **emulador oficial da Huawei** para simulação de redes e dispositivos.  
Ele permite **criar topologias de rede virtuais** com switches e roteadores Huawei, possibilitando testar **configurações reais de VRP (Versatile Routing Platform)**.

> ⚙️ O projeto foi testado utilizando o **Switch Huawei CE12800**, que executa o **VRP 8**, e também pode funcionar com roteadores Huawei compatíveis com o mesmo sistema.

O eNSP possibilita criar conexões entre **equipamentos virtuais e o PC físico** através da **nuvem de integração (VirtualBox Host-Only Network)**, tornando possível a comunicação entre o software de automação e o dispositivo Huawei.

---

## ☁️ Configuração da Nuvem (VirtualBox Host-Only Network)

A imagem abaixo representa a **configuração da nuvem** utilizada no eNSP para comunicação entre o **Huawei Network Automation Tool** e o **Switch CE12800**.

<p align="center">
  <img src="https://github.com/user-attachments/assets/1210101d-fb80-4bd6-b72a-8ce0c5ded28e" alt="Configuração da Nuvem eNSP" width="650">
</p>

> 🔹 É através dessa interface que o PC e o equipamento Huawei trocam dados pelos protocolos NETCONF e SSH.

---

## ⚙️ Tecnologias Utilizadas

<p align="center">
  <!-- Bibliotecas Python -->
  <img src="https://img.shields.io/badge/Paramiko-SSH%20Automation-blue?style=for-the-badge&logo=python&logoColor=white" alt="Paramiko">
  <img src="https://img.shields.io/badge/ncclient-NETCONF%20Integration-orange?style=for-the-badge&logo=python&logoColor=white" alt="ncclient">
  <img src="https://img.shields.io/badge/Tkinter-Custom%20UI-yellow?style=for-the-badge&logo=python&logoColor=white" alt="Tkinter">
  <img src="https://img.shields.io/badge/Logging%20%7C%20JSON%20%7C%20Threading-System%20Modules-lightgrey?style=for-the-badge&logo=python&logoColor=white" alt="Python Modules">
</p>

---

### 🧰 Ferramentas de Desenvolvimento

- 🐍 **Python 3.10+** — linguagem base do projeto  
- 💻 **Git Bash** — execução de comandos e geração de chaves RSA  
- 📘 **Jupyter Notebook** — análise modular e testes de código  

---

### 📦 Principais Bibliotecas Utilizadas

- 🔐 **Paramiko** — conexões seguras via SSHv2  
- 🔧 **ncclient** — integração com protocolo NETCONF  
- 🗝️ **Chaves RSA (ssh-keygen)** — autenticação sem senha  
- 🪟 **Tkinter / CustomTkinter** — interface gráfica moderna  
- 📜 **Logging / JSON / OS / threading** — controle de logs e multitarefas  

---


## 🧩 Estrutura e Módulos Principais

> ⚙️ Cada módulo foi projetado de forma independente, com foco em **automação, confiabilidade e segurança**.  

<p align="center">
  <table>
    <tr>
      <td align="center" width="45%">
        <strong>⚙️ Aplicar Configuração (NETCONF)</strong><br>
        <em>Envio de blocos XML diretamente ao dispositivo Huawei via NETCONF.</em><br><br>
        <a href="https://github.com/user-attachments/assets/e3917464-f98b-47ab-ae9f-29a771bda710">
          <img src="https://github.com/user-attachments/assets/e3917464-f98b-47ab-ae9f-29a771bda710" width="450" style="border-radius:10px; box-shadow:0 4px 12px rgba(0,0,0,0.3); transition: all 0.3s ease;">
        </a>
      </td>
      <td align="center" width="45%">
        <strong>💾 Backup e Extração (SSH)</strong><br>
        <em>Backup completo e extração segura da configuração via SSH.</em><br><br>
        <a href="https://github.com/user-attachments/assets/67fd8d7c-2ce2-4157-b432-490f42d485ba">
          <img src="https://github.com/user-attachments/assets/67fd8d7c-2ce2-4157-b432-490f42d485ba" width="450" style="border-radius:10px; box-shadow:0 4px 12px rgba(0,0,0,0.3); transition: all 0.3s ease;">
        </a>
      </td>
    </tr>
    <tr>
      <td align="center" width="45%">
        <strong>🧠 Console Interativo (SSH)</strong><br>
        <em>Terminal integrado com autenticação RSA e execução em tempo real.</em><br><br>
        <a href="https://github.com/user-attachments/assets/cb599568-ddc5-421c-9007-e523d1c65fd5">
          <img src="https://github.com/user-attachments/assets/cb599568-ddc5-421c-9007-e523d1c65fd5" width="450" style="border-radius:10px; box-shadow:0 4px 12px rgba(0,0,0,0.3);">
        </a>
      </td>
      <td align="center" width="45%">
        <strong>📡 Testes de Conectividade</strong><br>
        <em>Execução de ping e traceroute com retorno visual em tempo real.</em><br><br>
        <a href="https://github.com/user-attachments/assets/7890b0f1-1004-4cdf-9395-521ed2ef5cd5">
          <img src="https://github.com/user-attachments/assets/7890b0f1-1004-4cdf-9395-521ed2ef5cd5" width="450" style="border-radius:10px; box-shadow:0 4px 12px rgba(0,0,0,0.3);">
        </a>
      </td>
    </tr>
    <tr>
      <td align="center" width="45%">
        <strong>🔌 Conexões (Configuração)</strong><br>
        <em>Configuração e validação dos parâmetros NETCONF e SSH com autenticação RSA.</em><br><br>
        <a href="https://github.com/user-attachments/assets/d5206281-16cc-4839-a1cc-1d4fab98909b">
          <img src="https://github.com/user-attachments/assets/d5206281-16cc-4839-a1cc-1d4fab98909b" width="450" style="border-radius:10px; box-shadow:0 4px 12px rgba(0,0,0,0.3);">
        </a>
      </td>
      <td align="center" width="45%">
        <strong>📜 Logs e Diagnósticos</strong><br>
        <em>Registro detalhado de eventos, conexões e execuções.</em><br><br>
        <a href="https://github.com/user-attachments/assets/65fa767d-d9c4-4519-b144-c0eff60ae5bc">
          <img src="https://github.com/user-attachments/assets/65fa767d-d9c4-4519-b144-c0eff60ae5bc" width="450" style="border-radius:10px; box-shadow:0 4px 12px rgba(0,0,0,0.3);">
        </a>
      </td>
    </tr>
  </table>
</p>

---

✨ *Clique para visualizar em tamanho completo.*


## 🖥️ Demonstração da Ferramenta

Abaixo é apresentado o **Huawei Network Automation Tool** em execução, demonstrando os principais módulos integrados na interface gráfica:

<p align="center">
  <img src="./screenshots/app_interface_demo.png" alt="Interface principal da ferramenta" width="750">
</p>

> ✅ Interface desenvolvida em **CustomTkinter**, com suporte a **execução paralela**, **validação em tempo real** e **integração direta com NETCONF e SSH**.

---

## 🔧 Configurações Necessárias no Equipamento Huawei

As configurações abaixo permitem a comunicação entre o **software** e o **equipamento Huawei**, habilitando os serviços NETCONF e SSH, além de definir a interface de gerenciamento.

### 🧩 Habilitar NETCONF (ncclient)
```bash
snetconf server enable
ssh user netconf
ssh user netconf authentication-type password
ssh user netconf service-type snetconf
netconf
 protocol inbound ssh port 830
 quit
aaa
 local-user netconf password irreversible-cipher Huawei12#$
 local-user netconf service-type ssh
 local-user netconf level 3
 quit
```

### 🔐 Habilitar SSH e autenticação por chave RSA (Paramiko)
```bash
stelnet server enable
user-interface vty 0 4
 authentication-mode aaa
 protocol inbound ssh
 user privilege level 3
 quit
aaa
 local-user python password irreversible-cipher Huawei12#$
 local-user python user-group manage-ug
 local-user python service-type ssh
 quit
ssh user python
ssh user python authentication-type rsa
ssh user python service-type stelnet
rsa peer-public-key rsa01 encoding-type openssh
 public-key-code begin
  #Insira sua chave pública aqui#
  public-key-code end
 peer-public-key end
ssh user python assign rsa-key rsa01
```

### 🌐 Ativar Interface de Gerenciamento
```bash
interface Vlanif1
 ip address 192.168.56.100 255.255.255.0
 undo shutdown
 quit

interface GE 1/0/0
 undo shutdown
 quit
```

> ⚠️ A interface **Vlanif1** é a responsável pela comunicação com o PC via **VirtualBox Host-Only Network (192.168.56.0/24)**.

---

## 🗝️ Geração da Chave RSA

Execute o seguinte comando para gerar as chaves de autenticação:

```bash
ssh-keygen -t rsa
```

Depois visualize sua **chave pública** com:

```bash
cat /c/Users/Joseffer/.ssh/id_rsa.pub
```

Copie o conteúdo e cole dentro do equipamento Huawei, no trecho:
```
public-key-code begin
  <sua_chave_publica_aqui>
public-key-code end
```

---

## 🚀 Conclusão

O projeto **Huawei Network Automation Tool** demonstra a aplicabilidade prática da **automação em redes corporativas**, oferecendo benefícios essenciais como:

- ✅ **Redução de erros humanos**  
- ⚡ **Maior eficiência e produtividade**  
- 🧩 **Centralização das tarefas de administração**  
- 🔒 **Segurança e rastreabilidade em todas as operações**

Durante os testes no **eNSP**, o sistema apresentou resultados estáveis e comunicação segura entre o **PC Host** e o **Switch Huawei CE12800** via **NETCONF** e **SSH**.

---

## 🔮 Melhorias Futuras

- 🚀 **Otimização de desempenho geral** e redução no tempo de resposta  
- 🧱 **Novos módulos administrativos** e de diagnóstico em tempo real  
- 💬 **Dicas contextuais interativas** e pop-ups informativos  
- 🔐 **Criptografia de backups automáticos**  
- 🎨 **Interface modernizada com temas claros e escuros**  

---

## 🙏 Agradecimentos

Agradeço ao **IFPB - Campus Campina Grande** e ao meu orientador **Dr. Prof. Marcelo Portela Sousa**, pelo apoio, orientação e incentivo durante o desenvolvimento deste projeto.

---

## 👨‍🎓 Autor e Orientação

**Autor:** Joseffer Maxwel Oliveira das Mercês  
**Curso:** Tecnologia em Telemática — *IFPB Campus Campina Grande*  
**Orientador:** Dr. Prof. Marcelo Portela Sousa  

---

## 📜 Licença

Distribuído sob a **Licença MIT**.  
Consulte o arquivo [`LICENSE`](./LICENSE) para mais detalhes.

---

## 📬 Contato & Mídias

<p align="center">
  <a href="mailto:joseffermax1472@gmail.com?subject=Contato%20-%20Huawei%20Network%20Automation%20Tool">
    <img src="https://img.shields.io/badge/Email-joseffermax1472%40gmail.com-red?style=for-the-badge&logo=gmail&logoColor=white" alt="Email">
  </a>
  <a href="https://www.linkedin.com/in/joseffer-maxwel-4309ab243">
    <img src="https://img.shields.io/badge/LinkedIn-Joseffer%20Maxwel-blue?style=for-the-badge&logo=linkedin" alt="LinkedIn">
  </a>
  <a href="http://lattes.cnpq.br/2695955591585329">
    <img src="https://img.shields.io/badge/Lattes-Joseffer%20Maxwel-lightgrey?style=for-the-badge&logo=academia" alt="Lattes">
  </a>
  <a href="https://www.credly.com/users/joseffer-maxwel">
    <img src="https://img.shields.io/badge/Credly-Joseffer%20Maxwel-orange?style=for-the-badge&logo=credly" alt="Credly">
  </a>
  <a href="https://github.com/joseffermax">
    <img src="https://img.shields.io/badge/GitHub-joseffermax-black?style=for-the-badge&logo=github" alt="GitHub">
  </a>
</p>

---

<h2 align="center">⚙️ “Automação é o caminho para redes mais seguras, rápidas e inteligentes.” 🚀</h2>

<p align="center">
  <img src="https://github.com/itsksaurabh/itsksaurabh/raw/master/assets/Developer.gif" width="250">
</p>
