# 🛡️ Política de Segurança — LegendClient

A segurança e a privacidade das credenciais da comunidade de **Legend Online**, **Wartune** e **Legend Remake** são prioridades fundamentais no desenvolvimento do **LegendClient**.

## 🔒 Arquitetura de Segurança de Dados
- **Armazenamento de Senhas Local:** O LegendClient **não** armazena credenciais em servidores remotos próprios. Todas as senhas salvas são mantidas exclusivamente no computador do usuário.
- **Criptografia Windows DPAPI:** A retenção de senhas utiliza a API de Proteção de Dados nativa do SO (`Data Protection API - DPAPI`), garantindo que os dados fiquem inacessíveis para outras contas do Windows ou softwares terceiros.
- **Comunicação Segura:** Todas as chamadas de autenticação e requisições aos servidores oficiais da 7Road, Oasis Games e parceiros utilizam estritamente o protocolo cifrado **HTTPS/TLS**.
- **Execução do Flash ActiveX:** O componente Flash é executado em escopo local e contido (`registration-free`), sem modificação do Registro do Windows.

## 🚨 Reportando Vulnerabilidades
Caso encontre qualquer falha de segurança, problema no armazenamento de sessão ou comportamento suspeito no cliente:

1. **Não abra uma Issue pública** para tratar de potenciais vulnerabilidades de segurança.
2. Envie os detalhes técnicos com passos para reprodução diretamente pelo canal oficial do criador no YouTube: [@PetaLegend](https://youtube.com/@petalegend) ou acesse o formulário no [Site Oficial](https://www.legendclient.com.br/).

---
*Agradecemos por ajudar a manter a comunidade do LegendClient segura!*