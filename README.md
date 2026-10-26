# LegendClient — Launcher Oficial para Legend Online, Legend Remake e Wartune

[![Site Oficial](https://img.shields.io/badge/Site%20Oficial-legendclient.com.br-ff8a1f?style=for-the-badge&logo=googlechrome&logoColor=white)](https://www.legendclient.com.br/)
[![Versão Atual](https://img.shields.io/badge/Versão-3.0.4-brightgreen?style=for-the-badge)](https://www.legendclient.com.br/)
[![Plataforma](https://img.shields.io/badge/Plataforma-Windows%2010%20%7C%2011-blue?style=for-the-badge&logo=windows)](https://www.legendclient.com.br/)
[![Idiomas](https://img.shields.io/badge/Idiomas-PT--BR%20%7C%20EN%20%7C%20ES%20%7C%20TR-orange?style=for-the-badge)](https://www.legendclient.com.br/)

O **LegendClient** (também conhecido como **Legend Online By Peta**) é a solução desktop definitiva e de alta performance desenvolvida em C# para execução de **Legend Online**, **Legend Remake** e **Wartune** no PC. 

Projetado do zero para substituir navegadores descontinuados, o cliente traz o **Flash Player pré-instalado e liberado**, gerenciamento nativo de **múltiplas contas simultâneas**, suporte a **Alto FPS (até 240 FPS)** e sincronização automática de servidores oficiais e mundos da comunidade.

👉 **Download oficial e informações do projeto:** [https://www.legendclient.com.br/](https://www.legendclient.com.br/)

---

> **Aviso de Projeto Independente:** O LegendClient é um projeto desenvolvido de forma autônoma pela comunidade por [@PetaLegend](https://youtube.com/@petalegend). Não possui vínculo comercial, afiliação direta ou patrocínio com a 7Road, Oasis Games, Elex ou demais operadoras do jogo. Todas as marcas registradas, nomes de servidores e recursos gráficos pertencem aos seus respectivos detentores.

---

## 📋 Estado Atual do Projeto (v3.0.4)

| Módulo / Funcionalidade | Status | Descrição Técnica |
| :--- | :--- | :--- |
| **Flash ActiveX Integrado** | ✅ Ativo | Subprocesso *registration-free* sem necessidade de instalação externa ou configuração de navegador. |
| **Engine de Alto FPS** | ✅ Ativo | Desbloqueio da taxa limite nativa (25 FPS) para **60, 90, 120, 144 e 240 FPS** com limitação inteligente de carga. |
| **Gestor Multi-Contas** | ✅ Ativo | Sistema de cartões para centenas de contas, busca rápida, filtro por plataforma e marcadores de favoritas. |
| **Catálogo de Mundos** | ✅ Ativo | Legend Online BR, España, Türkiye, Clássico, Legend Remake e Wartune (7Road) unificados. |
| **Reconexão Automática** | ✅ Ativo | Monitoramento de socket e reautenticação automática pós-queda de conexão (Legend Remake). |
| **Cofre de Credenciais** | ✅ Ativo | Criptografia local simétrica via **Windows Data Protection API (DPAPI)**. |
| **Atualizador Automático** | ✅ Ativo | Consulta assíncrona do repositório, validação de integridade por hash SHA-256 e aplicação *per-user*. |
| **Central de Ferramentas** | ✅ Ativo | Guia da Dimensão, Modo Turbo para PCs fracos, atalhos globais e utilitários para apoiadores. |
| **Discord Rich Presence** | ✅ Ativo | Integração RPC exibindo o status do personagem, mundo e servidor atual no perfil do Discord. |
| **Localização Multilíngue** | ✅ Ativo | Suporte completo a **Português (PT-BR)**, **Inglês (EN-US)**, **Espanhol (ES-ES)** e **Turco (TR-TR)**. |

---

## 🛠️ Arquitetura e Engenharia de Software

O cliente foi arquitetado para priorizar estabilidade e baixo consumo de memória RAM, executando o contêiner de renderização Flash de forma isolada do processo principal da interface.

```
┌────────────────────────────────────────────────────────────────────────┐
│                   LegendClient Principal (C# / .NET)                   │
├────────────────────────────────────────────────────────────────────────┤
│ ┌─────────────────────────┐ ┌───────────────────┐ ┌──────────────────┐ │
│ │   Gestor de Contas & UI │ │ Central de Tools  │ │ Auto-Updater /   │ │
│ │   (Filtros / Favoritas) │ │ (Guia Dimensão)   │ │ Integridade      │ │
│ └────────────┬────────────┘ └─────────┬─────────┘ └────────┬─────────┘ │
└──────────────┼────────────────────────┼────────────────────┼───────────┘
               │                        │                    │
               ▼                        ▼                    ▼
┌───────────────────────────┐ ┌───────────────────┐ ┌──────────────────┐
│ Windows Credential Store  │ │ Discord RPC API   │ │ Hub JSON /       │
│ (DPAPI Criptografia)      │ │ Integration       │ │ Servidores API   │
└───────────────────────────┘ └───────────────────┘ └──────────────────┘
               │
               ▼
┌────────────────────────────────────────────────────────────────────────┐
│            Instâncias Isoladas de Renderização do Jogo                 │
│  ┌───────────────────────┐   ┌───────────────────────┐                 │
│  │ Conta 1 (AxHost/Flash)│   │ Conta N (AxHost/Flash)│                 │
│  └───────────────────────┘   └───────────────────────┘                 │
└────────────────────────────────────────────────────────────────────────┘
```

### Principais Destaques de Código:
1. **Contêiner AxHost & Registration-Free ActiveX:** O Flash Player é carregado localmente através de manifesto isolado (`Flash.manifest`), sem modificar o Registro do Windows (`HKLM/HKCU`) do usuário e impedindo conflitos no sistema operacional.
2. **Sistema de Criptografia DPAPI:** As credenciais e dados sensíveis de acesso são encriptados utilizando a chave mestra da sessão do Windows do próprio usuário. Nenhuma senha é transmitida para servidores terceiros ou mantida em texto limpo.
3. **Mecanismo de Desbloqueio de FPS:** Interceptação do timer do loop de quadros do ambiente Flash, permitindo taxas suaves de até 240 FPS com alternância automática de desempenho caso a janela perca o foco ou o sistema apresente alta carga de processamento.

---

## 📂 Estrutura de Dados Locais

Todos os arquivos mutáveis, perfis e configurações do aplicativo são gravados estritamente na pasta do perfil do usuário (`%LocalAppData%\LegendClient`):

```text
%LocalAppData%\LegendClient\
├── cache\
│   └── server-catalogs.json     # Cache dos servidores oficiais e mundos ativos
├── data\
│   ├── profiles.json            # Perfis de conta, avatares locais e preferências
│   └── settings.json            # Configurações de idioma, FPS e estado de áudio
├── updates\
│   └── LegendOnlineByPeta_Setup.exe # Artefatos de atualização validados
└── logs\
    └── client-exception.log     # Logs de exceção para diagnóstico avançado
```

---

## ⚡ Instalação e Requisitos do Sistema

### Requisitos Mínimos:
* **Sistema Operacional:** Windows 10 ou Windows 11 (64-bit)
* **Processador:** Dual-Core 2.0 GHz ou superior
* **Memória RAM:** 2 GB de RAM disponível
* **Privilégios:** Instalação *per-user* (Não requer direitos de Administrador)

### Instruções de Instalação:
1. Acesse o site oficial: [www.legendclient.com.br](https://www.legendclient.com.br/)
2. Baixe o pacote comprimido (`.zip`).
3. Extraia o conteúdo para uma pasta de sua preferência.
4. Execute o arquivo `LegendOnlineByPeta_Setup.exe`.
5. Após instalado, as atualizações futuras serão baixadas e aplicadas automaticamente.

---

## 🔨 Instruções para Desenvolvedores (Build)

Caso deseje compilar o projeto a partir do código-fonte:

### Pré-requisitos:
* Windows 10/11 x64
* Visual Studio 2022 (com suporte a desenvolvimento Desktop .NET / C#)
* SDK do .NET Framework / .NET Desktop configurado

### Comandos de Compilação:

```powershell
# 1. Clonar o repositório
git clone https://github.com/petadeteta22/legend-online-by-peta.git
cd legend-online-by-peta

# 2. Restaurar dependências
dotnet restore

# 3. Compilar em modo Release
dotnet build --configuration Release

# 4. Executar os testes unitários
dotnet test --configuration Release
```

---

## 🌐 Links Importantes e Comunidade

* **Site Oficial do Launcher:** [https://www.legendclient.com.br/](https://www.legendclient.com.br/)
* **Canal do Criador no YouTube:** [@PetaLegend](https://youtube.com/@petalegend)
* **Apoio ao Projeto no LivePix:** [livepix.gg/peta](https://livepix.gg/peta)

---

<p center align="center">
  <b>LegendClient — Desenvolvido por Peta para a comunidade de Legend Online, Remake e Wartune.</b><br>
  <i>© 2026 Legend Online By Peta. Todos os direitos de marca pertencem aos seus respectivos proprietários.</i>
</p>