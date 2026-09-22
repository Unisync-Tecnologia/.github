# 🔒 Diretrizes Globais de Privacidade e LGPD na Saúde

Este documento estabelece os pilares fundamentais de conformidade com a **Lei Geral de Proteção de Dados (Lei nº 13.709/2018)** aplicados ao desenvolvimento do ecossistema *de software pela Unisync Tecnologia. 

Tratamos **Dados Pessoais Sensíveis de Saúde** e, por isso, a privacidade está integrada por padrão (*Privacy by Design*) em todo o nosso ciclo de desenvolvimento de software.

## 🛡️ Pilares Práticos para os Desenvolvedores

Todo código escrito para a Unisync deve respeitar rigorosamente as seguintes diretrizes:

### 1. Minimização de Dados
* Solicite e armazene apenas o estritamente necessário para a finalidade médica ou administrativa do sistema (ex: não solicite dados que não serão usados no prontuário ou faturamento).

### 2. Anonimização e Criptografia
* **Dados em repouso:** Todas as tabelas de banco de dados que contenham informações de pacientes (nomes, CPFs, diagnósticos, laudos) devem utilizar mecanismos de criptografia.
* **Dados em trânsito:** É obrigatório o uso de conexões seguras e criptografadas (HTTPS/TLS) para qualquer comunicação entre cliente, API e servidores.
* **Ambientes de Teste:** É terminantemente **proibido** utilizar dados reais de pacientes em ambientes de homologação, staging ou testes locais. Utilize sempre geradores de dados fictícios.

### 3. Controle de Acesso Restrito (RBAC)
* O código deve prever níveis hierárquicos de permissão claros. Um perfil administrativo não deve ter acesso visual a laudos clínicos se a função dele for apenas o faturamento financeiro.
* Implementar trilhas de auditoria (*logs*) imutáveis para registrar **quem** acessou determinado prontuário ou laudo e **quando** o fez.

### 4. Gestão de Logs Seguros
* Nunca registre dados sensíveis do paciente (como resultados de exames ou documentos) nos logs de erro do sistema (ex: console do servidor, ferramentas de monitoramento de APM). Logs servem apenas para rastrear o comportamento da aplicação, não dados do usuário.

## 🚨 Resposta a Incidentes de Privacidade

Qualquer suspeita de vazamento de dados, exposição acidental de chaves de API ou falha de autorização em algum software deve ser imediatamente escalada de forma interna conforme o nosso arquivo `SECURITY.md`.

---
*A segurança do SyncLab garante a privacidade do paciente e a estabilidade jurídica dos nossos parceiros.*
