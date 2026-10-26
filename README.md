## 🔒 Spy Privado — Acesso Restrito
# 🔒 Projeto Para fins educativo

## 📷 Imagens:



# 🛡️ Análise Educacional: Análise de Vetores Trojan & Spyware

> **Aviso de Isenção de Responsabilidade (Disclaimer):** Este repositório destina-se exclusivamente a fins educacionais, acadêmicos e de pesquisa em segurança da informação. O conteúdo visa demonstrar mecanismos de defesa, engenharia social e análise comportamental de ameaças.

## 📋 Visão Geral

Este projeto aborda o estudo de caso de um **Trojan (Cavalo de Troia)** combinado com rotinas de **Spyware (Software Espião)** disfarçado de uma aplicação de suporte acadêmico/educacional legítima.

O objetivo é mapear como engenharia social e vetores de disfarce são utilizados para contornar a desconfiança do usuário final e como analistas de segurança podem identificar, conter e mitigar esse tipo de vetor.

---

## 🔍 Arquitetura da Ameaça
[ Usuário ] ──Instalação──> [ Interface Educacional (Fachada) ]
│
(Segundo Plano)
│
┌────────────────────────────┴────────────────────────────┐
▼                                                         ▼
[ Módulo Trojan ]                                        [ Módulo Spyware ]
├── Persistência no Registro                             ├── Keylogging (Captura de teclas)
└── Download de Payloads Secundários                     ├── Captura de Tela & Exfiltração
│                                                         │
└────────────────────────────┬────────────────────────────┘
│
▼
[ Servidor Command & Control (C2) ]

---

## ⚙️ Componentes Analisados

### 1. Interface de Fachada (Engodo)
* **Comportamento Visível:** Exibe simulados, flashcards ou dicionários interativos para criar sensação de legitimidade.
* **Mecanismo de Desvio:** Mantém uso mínimo de CPU/RAM em primeiro plano para não levantar suspeitas no Gerenciador de Tarefas.

### 2. Rotinas de Trojan (Cavalo de Troia)
* **Elevação de Privilégios:** Solicita acesso de administrador alegando necessidade de "atualização do banco de dados pedagógico".
* **Mecanismo de Persistência:** Criação de rotinas no registro do sistema (`HKCU\Software\Microsoft\Windows\CurrentVersion\Run`) ou tarefas agendadas.

### 3. Rotinas de Spyware (Espionagem)
* **Keylogger:** Interceptação de chamadas de API do sistema operacional para registro de digitação.
* **Exfiltração de Dados:** Coleta sistemática de arquivos locais (`.pdf`, `.docx`, credenciais salvas) e envio via requisições HTTPS criptografadas para o servidor C2.

---

## 🛡️ Estratégias de Detecção e Mitigação

| Vetor de Ataque | Regra / Indicador de Comprometimento (IoC) | Solução de Mitigação |
| :--- | :--- | :--- |
| **Persistência no Registro** | Chaves autorun não assinadas digitalmente | Monitoramento EDR / Restrição de Execução |
| **Comunicação C2** | Tráfego constante para IPs/Domínios de baixa reputação | Firewall / Inspeção de Pacotes (DPI) |
| **Coleta de Teclas** | Injeção de hooks de teclado sem assinatura | Proteção de Memória / Antivírus Comportamental |

---
