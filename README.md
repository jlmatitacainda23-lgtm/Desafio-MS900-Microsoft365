# Desafio MS-900: Módulo 01 - Identidade, Utilizadores e Grupos (Avançado)


Este repositório documenta a execução prática das atividades do Módulo 1 do **Microsoft 365 Fundamentals (MS-900)**. O foco foi a administração de identidades, governança de grupos e segurança no **Microsoft Entra ID** (Azure Active Directory).

##  Resumo da Implementação

Abaixo, detalho as fases executadas durante o laboratório, consolidando o aprendizado em administração de diretório.

---

###  1. Gestão de Utilizadores (Provisionamento)
Nesta fase, realizei a criação de identidades no diretório utilizando diferentes perfis de licença:

* **Utilizadores Padrão:** Provisionamento de 8 contas principais para a estrutura organizacional:
    * `user1- José Lucas`
    * `user2- Ariete dos Santos`
    * `user3- Infante Sofia Alice`
    * `user4- Luzia Chaves`
    * `user5- Cleber dos Santos`
    * `user6- Edvanio Domingos`
    * `user7- Aurora José`
    * `user8- Justo Capingala`
* **Contas de Estagiários (Unlicensed):** Criação de 2 utilizadores específicos sem atribuição de licença:
    * `user09- Mechaque Estagiário`
    * `user10- Suzana Estagiária`
* **Colaboração B2B (Externo):** Configuração de 1 utilizador externo (`user11- Parceiro Externo`) via Portal do Azure. Mesmo enfrentando desafios na interface do portal, a criação foi confirmada com sucesso.

###  2. Estrutura de Grupos e Licenciamento
Implementação de modelos de gestão coletiva para otimizar a administração:

* **Criação de Grupos de Segurança:** Estruturação de 5 grupos específicos:
    * `GRP-TI`
    * `GRP-VENDAS`
    * `GRP-FINANCEIRO`
    * `GRP-DIRECAO`
    * `GRP-ESTAGIARIOS`.
      
* **Group-based Licensing:** Atribuição automatizada de licenças para os grupos
* `GRP-TI`
* `GRP-VENDAS`
* `GRP-FINANCEIRO`.
* **Gestão de Grupos Dinâmicos:** Iniciei a configuração de pertença dinâmica editando os atributos de contacto da utilizadora `Sofia Alice` (Departamento: Vendas). 
    > **Nota Técnica:** A conclusão desta fase foi limitada devido a restrições de licenciamento (necessário Azure AD Premium P1/P2) no ambiente de teste, mas a lógica de implementação foi aplicada.

### 3. Segurança e Manutenção de Identidade
Execução de tarefas críticas de administração e segurança:

* **Bloqueio de Login:** Suspensão de acesso realizada com sucesso para o `user8- Justo Capingala`.
* **Self-Service Password Reset (SSPR):** Reposição forçada de password para a utilizadora `user7- Aurora José`, com configuração de troca obrigatória no próximo início de sessão.
* **Governança de UPN:** Alteração do **User Principal Name** do `user05- Cleber dos Santos` para `Financeiro-Central`.

###  4. Administração e Relatórios
* **Exportação de Dados:** Geração de relatório de todos os utilizadores do diretório em formato **CSV**.
* **RBAC (Role-Based Access Control):** Tentativa de atribuição da função de "Administrador de Utilizadores" ao `user1- José Lucas`.
    > **Nota Técnica:** Ação limitada por falta de permissões globais no sandbox de laboratório para alteração de Roles administrativas.

---

## Tecnologias Utilizadas
* **Microsoft Entra ID** (Azure Active Directory)
* **Microsoft 365 Admin Center**

---
*Documentação gerada para registro de progresso no percurso de certificação Microsoft 365.*




