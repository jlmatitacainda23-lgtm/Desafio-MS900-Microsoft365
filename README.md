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
# Relatório de Implementação: Módulo 3
## Exchange Online (Gestão Operacional)

Este relatório descreve as atividades de configuração e administração realizadas no Exchange Online para a organização LearnIT, focando em eficiência, segurança e colaboração.

---

###  Fase 1: Criação de Caixas Partilhadas (Shared Mailboxes)
Nesta etapa inicial, configurei endereços de correio eletrónico coletivos, como `financeiro@` e `suporte@`. Esta ação permitiu a otimização de custos, pois estas caixas não exigem licenças pagas, e centralizou a comunicação dos departamentos, permitindo que vários membros respondam a partir de um único endereço profissional.

###  Fase 2: Atribuição de Membros e Gestão de Permissões
Procedi à configuração de acessos para as caixas partilhadas, delegando privilégios à utilizadora Ana Paula Ferreira. Foram atribuídas permissões de "Full Access" (Leitura e Gestão) e "Send As" (Enviar como). Esta configuração elimina a partilha de passwords e garante que apenas pessoal autorizado aceda a dados sensíveis, mantendo a conformidade da empresa.

###  Fase 3: Transformação de Conta em Caixa Partilhada
Converti uma conta de utilizador comum para o formato de caixa partilhada através do Centro de Administração. O objetivo principal foi a poupança de recursos de licenciamento e a preservação do histórico de e-mails antigos, permitindo que a equipa continue a gerir a conta de forma organizada sem custos adicionais.

###  Fase 4: Criação de Contacto Externo
Adicionei parceiros e fornecedores externos à lista de contactos global da organização. Esta configuração facilita a comunicação interna, pois o e-mail desses parceiros aparece automaticamente para todos os colaboradores ao redigirem mensagens, tornando o fluxo de trabalho mais simples e profissional.

###  Fase 5: Configuração de Respostas Automáticas
Ativei mensagens de resposta automática na caixa do Financeiro para remetentes internos e externos. Esta funcionalidade garante um feedback imediato aos utilizadores, informando que a mensagem foi recebida e será tratada em breve, o que eleva o nível de profissionalismo no atendimento.

###  Fase 6: Regras de Encaminhamento
Configurei o sistema para que todos os e-mails recebidos numa caixa partilhada sejam encaminhados automaticamente para um utilizador específico. Esta regra assegura que mensagens críticas sejam visualizadas rapidamente pelo gestor responsável, evitando que pedidos fiquem esquecidos em caixas de entrada gerais.

###  Fase 7: Segurança e Protocolos de Correio
Para reforçar a proteção das contas, desativei os protocolos antigos POP e IMAP. Esta medida de segurança protege a organização contra invasões, garantindo que os utilizadores utilizem apenas aplicações modernas e seguras do Microsoft 365 para aceder ao correio eletrónico.

###  Fase 8: Grupo de Segurança com E-mail
Criei o grupo "Direção_Segura", que combina permissões de segurança com capacidades de correio eletrónico. Este grupo facilita a comunicação em massa com a equipa e assegura que o acesso a documentos importantes seja restrito apenas a pessoas autorizadas, organizando a gestão da empresa.

###  Fase 9: Verificação de Limites de Envio
Acedi às definições de restrição no Centro de Administração do Exchange para validar os limites de tamanho de mensagens na conta Financeiro. Verifiquei que os limites estão fixados em aproximadamente 35 MB para envio e 36 MB para receção, garantindo que a caixa opere de forma estável e dentro dos parâmetros da organização.

###  Fase 10: Consulta de Logs de Envio (Message Trace)
Concluí o módulo utilizando a ferramenta de rastreamento de mensagens para monitorizar o fluxo de e-mails. Esta consulta em tempo real permitiu confirmar o estado de entrega das mensagens e validar que todo o sistema de comunicação da LearnIT está a funcionar corretamente e sem falhas.

---

# Relatório de Implementação: Módulo 4
## Microsoft Teams (Colaboração Avançada)

Este relatório detalha as configurações de governação, estrutura de equipas e políticas de comunicação implementadas no Microsoft Teams para garantir um ambiente de colaboração seguro e organizado.

---

###  Fase 1: Criação de Equipas no Teams
Nesta fase inicial, criei as equipas de **Vendas**, **TI** e **Financeiro** através da central de administração. Todas foram configuradas como **privadas**, garantindo que a comunicação interna seja restrita e que apenas membros autorizados de cada departamento tenham acesso ao conteúdo.

###  Fase 2: Criação de Canais Privados
Dentro da equipa Financeiro, implementei o canal restrito **"Direção_Privado"**. Este canal foi configurado com o nível de privacidade "Private", exibindo o ícone de cadeado. Esta configuração assegura que discussões estratégicas e documentos confidenciais fiquem acessíveis apenas a um subgrupo específico de membros autorizados.

###  Fase 3: Criação de Canais Partilhados
Finalizei a estruturação das equipas incluindo um espaço dedicado ao **"Projeto_Externo"**. Utilizei canais partilhados para permitir uma colaboração fluida entre diferentes departamentos e parceiros, mantendo sempre o nível de privacidade restrito para assegurar a segurança da plataforma.

###  Fase 4: Adição de Membros à Equipa
Procedi à gestão de utilizadores na equipa de **Vendas**, adicionando três colaboradores específicos. Esta ação foi fundamental para ativar o departamento comercial, permitindo o início imediato dos processos de comunicação e trabalho partilhado.

###  Fase 5: Definição de Proprietários (Owners)
Configurei um responsável adicional para a equipa de TI, alterando a sua função para **"Owner"** (Proprietário). Com esta gestão partilhada, garanti que a equipa possa ser administrada de forma independente, permitindo que outros utilizadores também giram permissões e membros.

###  Fase 6: Políticas de Mensagens Personalizadas
Criei a política **"Politica_Seguranca_Empresa"** no painel de administração. Esta política estabelece regras de comunicação mais rígidas, garantindo que as ferramentas de chat sejam utilizadas de forma profissional, segura e em conformidade com as normas da organização.

###  Fase 7: Controlo de Criação de Equipas
Configurei restrições ao nível da organização para impedir que utilizadores comuns criem equipas de forma descontrolada. Ao centralizar esta permissão na administração, garantimos um ambiente de trabalho limpo, organizado e focado exclusivamente nos departamentos oficiais.

###  Fase 8: Políticas de Reunião e Gravação
Ajustei as "Políticas de reunião" para garantir que a funcionalidade de gravação e transcrição esteja ativa. Esta configuração assegura que as reuniões importantes possam ser registadas automaticamente para consulta futura, facilitando a partilha de conhecimento entre a equipa.
