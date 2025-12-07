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

## 📦 Principais Bibliotecas Utilizadas

<p align="center">
  <img src="https://img.shields.io/badge/Paramiko-SSH%20Automation-blue?style=for-the-badge&logo=python&logoColor=white" alt="Paramiko">
  <img src="https://img.shields.io/badge/ncclient-NETCONF%20Integration-orange?style=for-the-badge&logo=python&logoColor=white" alt="ncclient">
  <img src="https://img.shields.io/badge/RSA%20Keys-ssh--keygen%20Auth-green?style=for-the-badge&logo=lock&logoColor=white" alt="Chaves RSA">
  <img src="https://img.shields.io/badge/Tkinter (ttk)-Modern%20UI-yellow?style=for-the-badge&logo=python&logoColor=white" alt="Tkinter (ttk)">
  <img src="https://img.shields.io/badge/Logging%20%7C%20JSON%20%7C%20Threading-System%20Modules-lightgrey?style=for-the-badge&logo=python&logoColor=white" alt="System Modules">
</p>

---

### 🧰 Ferramentas de Desenvolvimento

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.10%2B-blue?style=for-the-badge&logo=python&logoColor=white" alt="Python">
  <img src="https://img.shields.io/badge/Git%20Bash-Terminal%20CLI-orange?style=for-the-badge&logo=git&logoColor=white" alt="Git Bash">
  <img src="https://img.shields.io/badge/Jupyter-Notebook%20Environment-red?style=for-the-badge&logo=jupyter&logoColor=white" alt="Jupyter Notebook">
</p>

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
> O script foi testado no **Windows 10**, com suporte a **Tkinter (ttk)**.

---

## 🖥️ Demonstração da Ferramenta

Abaixo é apresentada a **Huawei Network Automation Tool** em execução, demonstrando todos os módulos integrados da interface gráfica.

<p align="center">

  <!-- Vídeo do YouTube (preview clicável) -->
  <a href="https://youtu.be/AT97F0RVphU" target="_blank">
    <img 
      src="https://img.youtube.com/vi/AT97F0RVphU/maxresdefault.jpg" 
      alt="Demonstração Huawei Network Automation Tool"
      width="750"
      style="border-radius: 10px;"
    >
  </a>

</p>

> 🎬 Clique na imagem acima para assistir à demonstração completa no YouTube.

> ✅ Interface desenvolvida em **Tkinter (ttk)**, com suporte a **execução paralela**, **validação em tempo real** e **integração direta com NETCONF e SSH**.

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

<p align="center">
  <sub>Projeto desenvolvido no âmbito do curso de <strong>Tecnologia em Telemática</strong> — Instituto Federal da Paraíba (IFPB) - Campus Campina Grande</sub>
</p>

<p align="center">
  <img src="https://github.com/itsksaurabh/itsksaurabh/raw/master/assets/Developer.gif" width="250">
</p>
