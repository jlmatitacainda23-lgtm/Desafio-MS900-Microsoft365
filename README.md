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

---
---
# Relatório de Implementação: Módulo 2
## Gestão de Licenças, Subscrições e Custos no Microsoft 365

Este relatório detalha as fases de auditoria, automação e governação aplicadas ao locatário (tenant) para otimização de recursos e segurança financeira.

---

###  Fase 1: Inventário de Ativos
Nesta etapa inicial, foi realizada uma auditoria no locatário para validar o inventário de ativos e garantir visibilidade total sobre o consumo de serviços. Através do Centro de Administração, foram identificados os seguintes estados de subscrição:

**Office 365 E5 (no Teams):** Atualmente num estado ativo, este produto conta com um total de 15 licenças compradas. Destas, 12 já foram atribuídas a utilizadores, restando apenas 3 licenças disponíveis para novas contratações.

**Windows 10/11 Enterprise E3:** Esta subscrição apresenta uma ampla margem de crescimento, com apenas 1 licença atribuída de um total de 15 disponíveis, mantendo o estado ativo no sistema.

**Microsoft Teams Enterprise:** À semelhança do Windows, este serviço possui 1 licença em uso e 14 licenças disponíveis para utilização imediata, garantindo a continuidade operacional.

> **Conclusão da Fase:** A auditoria permitiu identificar que o plano Office 365 E5 está próximo do limite de uso, sendo fundamental para a gestão de custos e para evitar a interrupção de serviços por falta de licenciamento.

---

###  Fase 2: Licenciamento Baseado em Grupo (Group-based Licensing)
O foco desta fase foi a transição do modelo de gestão manual para um modelo automatizado e escalável. Utilizando grupos de segurança (como o grupo TI), ativou-se a subscrição Office 365 E5 via herança.

Esta estratégia garante que qualquer novo colaborador adicionado ao grupo receba os serviços de produtividade de forma imediata. Na lógica de eficiência estabelecida, evitamos o cenário incorreto onde um utilizador gastaria duas licenças (manual + grupo), garantindo que apenas uma licença seja ocupada por utilizador.

---

###  Fase 3: Remoção de Licença Direta e Otimização
Realizou-se uma limpeza administrativa para eliminar redundâncias. No perfil do utilizador `user01-José Lucas`, detetou-se uma atribuição dupla. Ao remover a licença direta, o sistema validou que o utilizador manteve o acesso através do grupo. Esta ação corretiva devolveu com sucesso 1 unidade ao inventário geral, aumentando a disponibilidade de 3 para 4 licenças.

---

###  Fase 4: Análise Comparativa de Licenciamento
A análise entre os planos **Microsoft 365 Business Premium** e **Office 365 E3** revelou que a família Business possui um limite rigoroso de 300 utilizadores, fator decisivo para o planeamento de crescimento. 

Enquanto o Business Premium oferece uma solução de segurança "pronta a usar" com Intune e proteção avançada, o Office 365 E3 foca-se em alta capacidade de armazenamento, podendo necessitar de complementos para igualar a segurança de dispositivos do plano Business.

---

###  Fase 5 & 6: Auditoria e Projeção de Défice
Na Fase 5, a filtragem de utilizadores não licenciados identificou três contas (estagiários e parceiros) sem subscrições, prática essencial para o controlo de custos. Na Fase 6, projetou-se um cenário de crescimento: com apenas 3 licenças disponíveis, a contratação de 20 novos funcionários geraria um défice de 17 licenças, exigindo investimento imediato da empresa.

---

###  Fase 7: Identificação de Serviços e Bloqueio
Ao aceder às aplicações da utilizadora `Ana Paula Ferreira`, confirmou-se que os serviços estão em modo de "Leitura" (bloqueados para edição individual). Isto prova que a política de Group-based licensing está ativa, impedindo erros de gestão manual e garantindo que todos os membros do grupo possuam o mesmo conjunto de ferramentas.

---

###  Fase 8: Monitorização de Consumo e Atividade
Acedeu-se ao painel de Utilização para analisar a adoção dos serviços licenciados. Esta ferramenta permite extrair relatórios detalhados de utilizadores ativos por serviço (Exchange, Teams, SharePoint), sendo essencial para ajustar o licenciamento com base no uso real e evitar subscrições subutilizadas.

---

###  Fase 9: Governação e Segurança Financeira
Foi realizada uma alteração nas definições da organização para "Não permitir" avaliações e compras personalizadas por parte dos utilizadores. Esta ação evita o "Shadow IT" e garante que a aquisição de novas licenças seja feita exclusivamente pelo departamento de TI, assegurando o controlo total do orçamento.

---

###  Fase 10: Conclusão Técnica
Finalizou-se com sucesso a automação do licenciamento. Através de grupos de segurança, demonstrou-se que novos utilizadores recebem automaticamente os planos necessários via herança. Além disso, estabeleceram-se controlos de segurança e funções administrativas específicas (User Administrator e Billing Reader), garantindo uma operação eficiente e financeiramente segura do tenant.



----
