# Desafio MS-900: Módulo 1 – Identidade, Utilizadores e Grupos (Avançado)

Este repositório documenta a conclusão prática do Módulo 1, focado na administração avançada de identidades e governança dentro do ecossistema Microsoft 365.

## Atividades Realizadas

### 1. Gestão de Utilizadores
* **Criação de Utilizadores Padrão:** Provisionamento de 8 utilizadores seguindo a convenção de naming padrão.
* **Cenários de Estágio:** Criação de 2 utilizadores específicos para estágio, configurados sem atribuição de licença.
* **Colaboração B2B:** Criação de 1 utilizador externo com domínio de parceiro para testes de federação e acesso convidado.
* **Manutenção de Identidade:** Alteração de UPN (User Principal Name) de um utilizador e exportação da lista completa de utilizadores em formato CSV.

### 2. Administração de Grupos e Licenciamento
* **Estrutura Organizacional:** Criação de 5 grupos estratégicos:
    * `GRP-TI`
    * `GRP-VENDAS`
    * `GRP-FINANCEIRO`
    * `GRP-DIRECAO`
    * `GRP-ESTAGIARIOS`
* **Group-based Licensing:** Configuração de licenciamento automático baseado em grupo para 3 das unidades criadas.
* **Automação Dinâmica:** Implementação de um **Grupo Dinâmico** com regra baseada no atributo `Departamento = Vendas`.

### 3. Segurança e Controle de Acesso
* **Controle de Login:** Bloqueio preventivo de login para 1 utilizador.
* **Políticas de Password:** Configuração para forçar o reset de password no próximo logon do utilizador.
* **RBAC (Privilégios):** Atribuição da Role de **User Administrator** para gestão delegada de identidades.

##  Stack Técnica
* **Microsoft Entra ID** (Azure AD)
* **Microsoft 365 Admin Center**
* **Governança de Identidade**


*Laboratório concluído como parte do percurso de certificação Microsoft 365 Fundamentals.*






