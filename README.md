<h1 align="center">🤖 Huawei Network Automation Tool ⚙️</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Status-Concluído-brightgreen.svg" alt="Status do Projeto">
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

O projeto **Huawei Network Automation Tool** foi desenvolvido como parte do **Trabalho de Conclusão de Curso (TCC)** de Tecnologia em Telemática, com o objetivo de simplificar e automatizar tarefas de configuração e monitoramento de dispositivos de rede.

Em ambientes corporativos e acadêmicos, o gerenciamento manual via **CLI** pode ser demorado e propenso a erros. Essa ferramenta centraliza as principais rotinas de administração — como envio de configurações, coleta de backups e testes de conectividade — em uma interface unificada, segura e de fácil uso.

---

## ⚙️ Tecnologias Utilizadas

- 🐍 **Python 3**
- 🔐 **Paramiko** — Conexões seguras via SSHv2  
- 🔧 **ncclient** — Integração com protocolo NETCONF  
- 🗝️ **Chaves RSA** — Autenticação sem senha  
- 🪟 **Tkinter / CustomTkinter** — Interface gráfica da aplicação  
- 📜 **Logging / JSON / OS** — Armazenamento, logs e manipulação de arquivos

---

## 🧠 Arquitetura e Módulos Principais

A ferramenta foi estruturada de forma modular, garantindo escalabilidade e manutenção simples.

| Módulo | Função Principal | Descrição |
|--------|------------------|------------|
| **Aplicar Configuração** | Envio de blocos XML via NETCONF | Permite aplicar configurações diretamente nos dispositivos de rede, com suporte à edição dinâmica durante a execução. |
| **Gerar Backup** | Extração de configurações completas | Coleta e armazena as configurações atuais do dispositivo, salvando automaticamente em diretórios organizados. |
| **Console Interativo** | Execução manual de comandos SSH | Permite ao administrador enviar comandos diretamente, com retorno em tempo real na interface. |
| **Testes de Conectividade** | Ping e Traceroute integrados | Executa diagnósticos de conectividade e mostra os resultados de forma prática e visual. |
| **Gerenciamento de Credenciais** | Alteração dinâmica de login | As credenciais NETCONF e SSH podem ser modificadas sem reiniciar o aplicativo. |
| **Registro de Logs** | Auditoria e rastreabilidade | Todos os eventos e operações são registrados para consultas futuras e auditorias. |

---

## 🧪 Fase de Testes

A ferramenta foi validada em ambiente simulado com o **eNSP (Emulator Network Simulation Platform)**, da Huawei.  
Os testes confirmaram a comunicação estável entre os módulos, execução correta de comandos e extração de configurações completas.

📊 **Resultados:**
- ✅ Envio e aplicação bem-sucedida de blocos XML  
- ✅ Geração automática de backups em diretórios dedicados  
- ✅ Conectividade validada via ping e traceroute integrados  
- ✅ Logs gerados para todas as operações  
- ✅ Comunicação simultânea entre NETCONF e SSH sem conflito

---

---

## 📸 Interface da Aplicação

> As telas a seguir apresentam a interface principal e as janelas de configuração da ferramenta.

| Tela Principal | Aplicar Configuração | Teste de Conectividade |
|----------------|----------------------|------------------------|
| ![Tela Principal](./screenshots/main_window.png) | ![Configuração](./screenshots/config_window.png) | ![Conectividade](./screenshots/connectivity_window.png) |

---

## 📚 Fundamentação Técnica

A ferramenta foi desenvolvida com base em conceitos de **automação de redes**, **protocolos de gerenciamento remoto (NETCONF e SSH)** e **segurança em comunicação**.  
Essas tecnologias são amplamente utilizadas em ambientes profissionais para garantir **padronização, rastreabilidade e redução de falhas humanas** no gerenciamento de dispositivos.

---

## 🚀 Conclusão

O projeto **Huawei Network Automation Tool** demonstra a viabilidade da automação como suporte à administração de redes modernas.  
Seu desenvolvimento reforça a importância de integrar **segurança, eficiência e praticidade** em um único sistema.

A ferramenta apresenta potencial de expansão para:
- Integração com sistemas de versionamento (Git);
- Auditorias automatizadas de configuração;
- Monitoramento SNMP e API REST.

---

## 👨‍🎓 Autor e Orientação

**Autor:** Joseffer Maxwel Oliveira das Mercês  
**Curso:** Tecnologia em Telemática — *IFPB Campus Campina Grande*  
**Orientador:** Prof. Ewerton Rômulo Silva Castro  

---

## 📜 Licença

Distribuído sob a **Licença MIT**.  
Consulte o arquivo `LICENSE` para mais detalhes.

---

## 📬 Contato

- 📧 Email: [joseffermax1472@gmail.com](mailto:joseffermax1472@gmail.com)  
- 💼 LinkedIn: [Joseffer Maxwel](https://www.linkedin.com/in/joseffer-maxwel-4309ab243)  
- 🧠 Lattes: [Joseffer Maxwel Oliveira das Mercês](http://lattes.cnpq.br/2695955591585329)  
- 🏅 Credly: [Joseffer Maxwel Oliveira Das Merces](https://www.credly.com/users/joseffer-maxwel)

---

<h2 align="center">⚙️ “Automação é o caminho para redes mais seguras, rápidas e inteligentes.” 🚀</h2>

## 🧰 Estrutura do Projeto

