# Levantamento de requisitos: Sistema Devisate Construções
**Grupo composto por Kauã Teixeira de Andrade e Marcelo Amancio**
1. Requisitos Funcionais (RF)
Os requisitos funcionais descrevem as operações, comportamentos e regras de negócio concretas do sistema, organizados por atores e módulos.

Área Pública & Autenticação
RF01: O sistema deve exibir na página inicial uma vitrine de equipamentos cadastrados, permitindo a busca por nome e a filtragem por categoria ou status de disponibilidade sem exigir login prévio.

RF02: O usuário deve conseguir solicitar o cadastro no sistema informando nome completo, e-mail corporativo, CPF, telefone e senha de acesso.

RF03: O sistema deve permitir a autenticação do usuário mediante o fornecimento de e-mail e senha cadastrados.

RF04: O usuário deve conseguir solicitar a recuperação de senha via e-mail informando o e-mail cadastrado.

Área do Usuário (Solicitante/Colaborador)
RF05: O usuário deve conseguir visualizar e atualizar seus dados cadastrais (exceto CPF e perfil de acesso) e alterar sua senha no painel de perfil.

RF06: O usuário deve conseguir solicitar o agendamento de um ou mais equipamentos para um período específico, informando a data/hora de início, data/hora de término esperada e a obra/finalidade de uso.

RF07: O sistema deve verificar a disponibilidade do equipamento e impedir a confirmação de agendamentos cujas datas coincidam com reservas já aprovadas ou períodos de manutenção agendados.

RF08: O usuário deve conseguir acompanhar o status das suas solicitações de agendamento (Ex: Pendente, Aprovado, Recusado, Concluído) e consultar todo o seu histórico de empréstimos anteriores.

Área Administrativa & Operacional
RF09: O administrador deve conseguir gerenciar os usuários do sistema (incluindo criação, edição, inativação e atribuição de perfis como Administrador, Operador de Almoxarifado e Solicitante).

RF10: O operador deve conseguir cadastrar, editar e desativar categorias de equipamentos (Ex: Ferramentas Elétricas, Maquinário Pesado, Equipamentos de Proteção).

RF11: O operador deve conseguir cadastrar equipamentos informando nome, número de série/patrimônio, marca, modelo, categoria, estado de conservação e localização física de armazenamento (prateleira/galpão).

RF12: O operador deve conseguir avaliar solicitações pendentes de agendamento, podendo aprová-las ou recusá-las com a obrigatoriedade de registrar uma justificativa em caso de recusa.

RF13: O operador deve conseguir registrar a entrega física de um equipamento (início do empréstimo), vinculando o responsável, o estado inicial do equipamento e a assinatura/confirmação de retirada.

RF14: O operador deve conseguir registrar a devolução do equipamento no sistema, anotando o estado de conservação no retorno, eventuais avarias e registrando a baixa no empréstimo.

RF15: O operador deve conseguir cadastrar ordens de manutenção (preventiva ou corretiva) para um equipamento, alterando seu status automaticamente para "Em Manutenção" e especificando o motivo, custo estimado e data prevista de retorno.

RF16: O sistema deve exibir no Dashboard administrativo indicadores em tempo real, incluindo total de equipamentos por status (Disponível, Emprestado, Em Manutenção), agendamentos do dia e equipamentos com devolução em atraso.

RF17: O administrador deve conseguir gerar relatórios exportáveis (em PDF ou CSV) contendo o histórico de utilização de equipamentos, custos de manutenção por período e taxa de atraso por colaborador/obra.

2. Requisitos Não Funcionais (RNF)
Os requisitos não funcionais definem os critérios de qualidade, desempenho, segurança e disponibilidade que o sistema deve garantir durante sua execução.

RNF01 (Desempenho): O sistema deve carregar as páginas e responder às requisições de consulta do catálogo e dashboard em um tempo de resposta inferior a 2 segundos sob carga normal de operação.

RNF02 (Segurança/Criptografia): Todas as senhas dos usuários devem ser armazenadas no banco de dados com algoritmos de hash seguros (como BCrypt ou Argon2) com sal (salt), nunca em texto limpo.

RNF03 (Controle de Acesso): O sistema deve aplicar autorização baseada em perfis (RBAC), bloqueando o acesso direto por URL a recursos administrativos (como exclusão de usuários ou aprovação de agendamentos) para usuários com perfil Solicitante.

RNF04 (Usabilidade/Responsividade): A interface do sistema deve ser totalmente responsiva, adaptando-se para uso em computadores desktop, tablets e smartphones (iOS e Android) sem perda de funcionalidade.

RNF05 (Auditabilidade): O sistema deve manter um log auditável imutável de todas as operações sensíveis (criação, alteração de status de empréstimo, alteração de usuários e exclusões), registrando a data, hora e o ID do usuário responsável pela ação.

RNF06 (Disponibilidade): A aplicação deve manter um índice de disponibilidade (Uptime) de no mínimo 99,5% no horário comercial (das 06h às 20h), considerando o ambiente de produção em nuvem.

RNF07 (Integridade dos Dados): O banco de dados deve implementar transações ACID e restrições de chave estrangeira, impedindo a exclusão física de um equipamento que possua históricos vinculados de empréstimo ou manutenção (adotando exclusão lógica).

RNF08 (Usabilidade/Feedback): A interface deve fornecer mensagens explicativas claras e em linguagem amigável em caso de erro de validação (como formulários incorretos ou datas inválidas), destacando visualmente os campos com pendência em até 500ms após a submissão.
