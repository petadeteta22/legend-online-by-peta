# 📋 Histórico de Versões & Patch Notes — LegendClient

[![Site Oficial](https://img.shields.io/badge/Site_Oficial-legendclient.com.br-ff8a1f?style=for-the-badge&logo=googlechrome&logoColor=white)](https://www.legendclient.com.br/)
[![Versão Atual](https://img.shields.io/badge/Vers%C3%A3o-3.0.4-brightgreen?style=for-the-badge)](https://www.legendclient.com.br/)
[![Plataforma](https://img.shields.io/badge/Plataforma-Windows_10_%7C_11-blue?style=for-the-badge&logo=windows)](https://www.legendclient.com.br/)

Este documento registra todo o histórico de lançamentos, inclusão de novos ecossistemas de jogos, otimizações de motor gráfico e correções de segurança aplicadas ao **LegendClient (Legend Online By Peta)**.

> 🌐 **Download Oficial e Atualizações:** Para garantir a integridade dos binários e instalar o executável verificado, acesse sempre [https://www.legendclient.com.br/](https://www.legendclient.com.br/).

---

## 📑 Resumo de Releases

| Versão | Data de Lançamento | Principais Destaques | Status |
| :--- | :--- | :--- | :--- |
| **`v3.0.4`** | 16/10/2026 | Suporte ao Wartune, Gerenciador em Cartões e Nomes Oficiais | 🟢 Estável (Atual) |
| **`v3.0.2`** | 08/2026 | Multi-Janelas com isolamento de processo, Criptografia DPAPI, Discord RPC | 🟡 Legado |
| **`v3.0.0`** | 05/2026 | Arquitetura C# WinForms / CefSharp e Engine de Alto FPS (240 FPS) | 🟡 Legado |

---

## 🚀 [3.0.4] — 16/10/2026

### 🎮 Novos Mundos e Integrações de Servidor
* **Suporte Oficial ao Wartune:** Módulo dedicado ao título oficial da 7Road em janela própria, contendo seletor de servidores e retenção do último acesso por perfil.
* **Mapeamento de Servidores Oficiais:** Atualização do catálogo com identificação e nomes reais dos servidores (ex: *S1011 · Cristais de Vênus*).
* **Catálogo Dinâmico de Mundos:** Suporte nativo ao Legend Online (Brasil, Espanha, Turquia, Clássico) e Legend Remake sem necessidade de recompilação do launcher.

### 🎨 Interface e Experiência do Usuário (UI/UX)
* **Gerenciador de Contas em Cartões:** Redesenho da interface gráfica para seleção de perfis, com renderização assíncrona otimizada para manipular centenas de contas salvas sem perda de *frame rate*.
* **Filtros e Sistema de Favoritos:** Campo de busca em tempo real, filtros por plataforma e suporte à fixação de contas preferidas no topo da visualização.
* **Ocultação Inteligente de Topbar:** A barra superior de navegação é recolhida automaticamente assim que a requisição de carregamento do Flash é iniciada.

### ⚡ Desempenho e Engine Gráfica
* **Execução Nativa do Flash ActiveX:** O subprocesso ActiveX é liberado e configurado automaticamente na inicialização, eliminando solicitações de autorização manual.
* **Engine de FPS Adaptativa:** Algoritmo que gerencia a taxa de amostragem gráfica (60, 90, 120, 144 ou 240 FPS), aplicando redução de carga de renderização quando a aplicação está em segundo plano.
* **Rotina de Reconexão (Legend Remake):** Reautenticação automática e restauração de sessão em instâncias ativas após interrupções de rede ou reinício dos servidores.

### 🛡️ Segurança e Estabilidade
* **Validação de Integridade no Auto-Updater:** O módulo de atualização remota checa o tamanho e os arquivos da release antes de autorizar a execução do *setup*.
* **Ajuste de Dialogs:** Remoção de telas de confirmação repetitivas ao alternar entre instâncias ou trocar de mundo.

---

## 🛠️ [3.0.2] — 08/2026

### 🚀 Novidades
* **Isolamento de Processos Multi-Contas:** Execução simultânea de múltiplos perfis, em que cada janela opera sob um processo filho independente, prevenindo quedas globais por falhas de memória.
* **Discord Rich Presence:** Módulo de presença exibindo a versão, mundo e servidor ativo no perfil do Discord do usuário.

### 🛡️ Criptografia e Armazenamento
* **Integração com Windows DPAPI:** As credenciais salvas localmente passam a ser criptografadas utilizando a *Data Protection API* nativa do Windows, vinculadas à conta do usuário no sistema operacional.

---

## 🏗️ [3.0.0] — 05/2026

### 🚀 Refatoração do Core
* **Nova Arquitetura C# Desktop:** Transição do cliente para C# WinForms com container CefSharp, eliminando dependências de navegadores legados (Internet Explorer / Flash standalone antigo).
* **Remoção da Trava de 25 FPS:** Implementação de interceptação no loop de renderização do Flash, permitindo alcançar até 240 FPS em monitores de alta taxa de atualização.
* **Subprocesso Registration-Free:** Execução do plugin Flash em escopo estritamente local, sem alteração de chaves do Registro do Windows (`HKLM`/`HKCU`).

---

## 💡 Como Atualizar o LegendClient

1. **Via Auto-Updater (Recomendado):** O launcher identifica novas versões automaticamente ao iniciar. Basta confirmar a mensagem para aplicar a atualização sem perder seus perfis e configurações.
2. **Instalação Manual:** Baixe o arquivo `LegendOnlineByPeta_Setup.zip` diretamente no [Site Oficial](https://www.legendclient.com.br/) ou acesse a seção de [Releases do GitHub](https://github.com/petadeteta22/legend-online-by-peta/releases).