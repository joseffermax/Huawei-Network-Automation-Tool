<h1 align="center">🤖 Huawei Network Automation Tool ⚙️</h1>

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

## 🧩 Sobre o Projeto

O projeto **Huawei Network Automation Tool** foi desenvolvido como parte do **Trabalho de Conclusão de Curso (TCC)** do curso de **Tecnologia em Telemática** no **IFPB - Campus Campina Grande**.

O objetivo é **automatizar e simplificar** tarefas de configuração, backup e monitoramento de dispositivos Huawei, centralizando todas as funções em uma interface única e segura.  
A aplicação integra os protocolos **NETCONF** e **SSH**, com suporte a **autenticação RSA**, para garantir uma comunicação eficiente e confiável entre administrador e dispositivo.

---

## ⚙️ Tecnologias Utilizadas

- 🐍 **Python 3.10+**
- 🔐 **Paramiko** — conexões seguras via SSHv2  
- 🔧 **ncclient** — integração com protocolo NETCONF  
- 🗝️ **Chaves RSA (ssh-keygen)** — autenticação sem senha  
- 🪟 **Tkinter / CustomTkinter** — interface gráfica da aplicação  
- 📜 **Logging / JSON / OS / threading** — controle de logs, arquivos e execução paralela  

---

## 🧠 Arquitetura e Módulos Principais

A ferramenta foi projetada de forma **modular**, permitindo expansão, paralelismo e manutenção simples.  
Cada módulo executa uma função essencial para administração de redes.

| Módulo | Função Principal | Imagem |
|--------|------------------|--------|
| **Aplicar Configuração (NETCONF)** | Envio de blocos XML diretamente ao dispositivo Huawei via NETCONF. Permite alterações automatizadas e seguras. | ![NETCONF](./screenshots/netconf_module.png) |
| **Backup e Extração (SSH)** | Extração e salvamento da configuração do dispositivo via SSH, com suporte a backups automáticos. | ![Backup](./screenshots/backup_module.png) |
| **Console Interativo (SSH)** | Terminal integrado para execução de comandos manuais via sessão SSH autenticada por RSA. | ![Console](./screenshots/console_module.png) |
| **Testes de Conectividade** | Execução de ping e traceroute com exibição em tempo real. | ![Testes](./screenshots/test_module.png) |
| **Configurações Dinâmicas** | Edição e validação em tempo real dos parâmetros NETCONF e SSH, sem reiniciar o app. | ![Configurações](./screenshots/config_module.png) |
| **Logs do Sistema** | Armazena todos os eventos e ações executadas pela ferramenta. | ![Logs](./screenshots/logs_module.png) |

---

## 🧪 Configuração do Ambiente de Testes (eNSP Huawei)

O ambiente foi montado no **Huawei eNSP (Emulator Network Simulation Platform)**, utilizando roteadores **Huawei AR**.  
Abaixo estão os comandos necessários para habilitar os serviços **NETCONF** e **SSH** no equipamento.

---

## 🔹 Configuração do NETCONF

A configuração abaixo habilita o serviço **NETCONF** no dispositivo Huawei, permitindo que a aplicação envie blocos XML e execute automações de forma segura.

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

---

## 🔹 Configuração do SSH

Esta configuração habilita o serviço **SSHv2 (Stelnet)** no equipamento Huawei e vincula o usuário à **chave pública RSA** para autenticação segura.  

Por meio desse serviço, a aplicação é capaz de:

- 💾 **Realizar backups automáticos**  
- 🧠 **Executar comandos diretos via console interativo**  
- 📡 **Efetuar testes de conectividade (ping/traceroute)**  

```bash
stelnet server enable
user-interface vty 0 4
 authentication-mode aaa
 protocol inbound ssh
 user privilege level 3
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
🔑 **Observação:**

Substitua o conteúdo entre `public-key-code begin` e `end` pela **sua chave pública RSA** (`id_rsa.pub`).  

Essa chave deve corresponder à **chave privada** configurada no campo `key_path` do módulo **SSH** da aplicação.

---

## 🔹 Interface de Gestão (Exemplo)

A configuração abaixo define a **interface de gerenciamento (Vlanif1)** responsável pela comunicação entre o equipamento Huawei e a aplicação de automação.  
Essa interface deve estar ativa e acessível para permitir conexões via **NETCONF** e **SSH**.

```bash
interface Vlanif1
 ip address 192.168.56.100 255.255.255.0
 undo shutdown
 quit
```

---

## 🗝️ Geração da Chave RSA (para SSH)

Antes de executar o projeto, é necessário gerar um **par de chaves RSA** para autenticação segura via **SSH**.  
Essa chave garante uma comunicação criptografada entre o software e o equipamento Huawei, sem necessidade de senha manual.

Execute o seguinte comando no **Git Bash** (ou terminal equivalente):

```bash
ssh-keygen -t rsa
```
Durante o processo, será solicitado um **nome de arquivo** e, opcionalmente, uma **senha de proteção**.  

Por padrão, as chaves serão salvas no seguinte diretório:

```bash
C:\Users<seu_usuario>.ssh\
```

🔑 **A chave privada** (`id_rsa`) deve ser informada no campo `key_path` do módulo **SSH** dentro da aplicação.  
📋 **A chave pública** (`id_rsa.pub`) deve ser copiada para o dispositivo **Huawei**, no campo `public-key-code` da configuração SSH.

---

## 📦 Instalação e Dependências

Para instalar e executar o projeto **Huawei Network Automation Tool**, siga os passos abaixo:

1. **Clone o repositório oficial do projeto:**
   ```bash
   git clone https://github.com/joseffermax/Huawei-Network-Automation-Tool.git
   cd Huawei-Network-Automation-Tool

---

## 🧩 Dependências Principais

As principais bibliotecas utilizadas na aplicação são apresentadas abaixo.  
Certifique-se de instalá-las antes da execução do sistema.

```python
# -*- coding: utf-8 -*-
"""
Requisitos: Python 3.x, ncclient, paramiko, tkinter
"""

import os
import sys
import time
import threading
import subprocess
import tkinter as tk
from ncclient import manager
import paramiko
```

---

## 🧩 Execução

Para iniciar o programa, basta executar o comando abaixo no terminal:

```bash
python main.py

```
A interface gráfica será aberta automaticamente com **todos os módulos habilitados**.

Por padrão, o sistema utiliza **configurações de conexão pré-definidas** (armazenadas em memória), permitindo acesso imediato aos módulos de **teste e automação**.

Após a inicialização, acesse o módulo **⚙️ Conexões** dentro da aplicação para **editar e validar** os parâmetros de rede, como:

- 🌐 **Endereço IP / Host**  
- 🔌 **Portas (NETCONF e SSH)**  
- 👤 **Usuários e Senhas**  
- 🗝️ **Caminho da Chave RSA** (para autenticação SSH segura)

Essas alterações podem ser aplicadas **em tempo real**, sem a necessidade de reiniciar o aplicativo.

---

## 🚀 Conclusão

O projeto **Huawei Network Automation Tool** demonstra a aplicabilidade prática da **automação em redes corporativas**, oferecendo benefícios essenciais como:

- ✅ **Redução de erros humanos**  
- ⚡ **Maior eficiência e produtividade**  
- 🧩 **Centralização das tarefas de administração**  
- 🔒 **Segurança e rastreabilidade em todas as operações**

A ferramenta provou sua eficácia durante os testes, integrando de forma estável os protocolos **NETCONF** e **SSH**, além de proporcionar um ambiente gráfico intuitivo e seguro para administradores de rede.

---

## 🔮 Melhorias Futuras

O desenvolvimento contínuo da ferramenta visa torná-la ainda mais robusta e completa.  
Entre as próximas atualizações planejadas, destacam-se:

- 🚀 **Otimização de desempenho geral** para maior responsividade  
- 🧱 **Adição de novos módulos administrativos** e de monitoramento  
- 💬 **Pop-ups interativos** com dicas e instruções contextuais  
- 🔐 **Criptografia nos backups automáticos** para reforço da segurança  
- 🎨 **Interface gráfica aprimorada**, fluida e com design mais moderno  

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
  <a href="mailto:joseffermax1472@gmail.com">
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
