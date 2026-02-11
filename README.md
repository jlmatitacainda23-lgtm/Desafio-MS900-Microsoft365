# Desafio MS-900: Módulo 01 - Identidade e Acesso

Este repositório contém o registro das atividades práticas realizadas durante o estudo do módulo de Identidade do **Microsoft 365 Fundamentals (MS-900)**. O foco principal foi a administração do **Microsoft Entra ID** (antigo Azure Active Directory).

## 📋 Resumo das Atividades

Abaixo estão detalhadas as etapas configuradas no ambiente de laboratório, incluindo os usuários e grupos específicos criados:

###  Gestão de Utilizadores e Identidade
* **Criação de Utilizadores Padrão:** Provisionamento de 8 contas principais (José Lucas, Ariete dos Santos,Sofia Alice, Luzia Chaves, Cleber dos Santos, Edvanio Domingos, Aurora José e Justo Capingala).
* **Utilizadores de Estágio:** Criação de contas específicas sem atribuição de licença para os usuários Mechaque Estagiário e Suzana Estagiária.
* **Acesso Externo (B2B):** Configuração do `user11-Parceiro Externo` via portal do Azure, superando desafios de navegação e permissões na interface.
* **Manutenção de Atributos:** Alteração do **UPN (User Principal Name)** do `user05-Cleber dos Santos` para `Financeiro-Central`, visando a padronização do diretório.
* **Segurança de Conta:** * Bloqueio de login realizado com sucesso para o usuário Justo Capingala.
    * Reposição de password para Aurora José, configurada com senha automática e exigência de troca no primeiro acesso.

###  Grupos e Licenciamento Automático
* **Estrutura de Grupos:** Criação de 5 Grupos de Segurança:
* `GRP-TI`
* `GRP-VENDAS`
* `GRP-FINANCEIRO`
* `GRP-DIRECAO`
* `GRP-ESTAGIARIOS`.
* **Licenciamento Baseado em Grupo:** Atribuição bem-sucedida de licenças do Microsoft 365 para os grupos
* `GRP-TI`
* `GRP-VENDAS`
* `GRP-FINANCEIRO`.
* **Grupos Dinâmicos:** Preparação do ambiente através da edição de atributos de contacto (Departamento: Vendas) para a utilizadora Sofia Alice. A implementação final foi limitada por restrições de licenciamento do ambiente de laboratório.

### Governança e Administração
* **RBAC (Role-Based Access Control):** Tentativa de atribuição da Role de "Administrador de Utilizadores" ao utilizador José Lucas. Ação devidamente documentada, embora limitada por permissões de conta no sandbox.
* **Relatórios:** Exportação da lista completa de utilizadores e dados do diretório em formato **CSV** para fins de auditoria e conformidade.

##  Tecnologias Utilizadas
* **Microsoft Entra ID** (Azure Active Directory)
* **Microsoft 365 Admin Center**

*Documentação gerada como parte do progresso no Desafio MS-900.*





