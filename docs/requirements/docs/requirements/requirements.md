
---

# Visualização do docs/requirements/requirements.md no GitHub

```markdown
# Documento de Requisitos - Sistema de Gestão de Biblioteca Universitária

## 1. Requisitos Funcionais (RF)

### 1.1 Módulo de Autenticação e Autorização
- **RF001**: O sistema deve permitir login com matrícula e senha para alunos
- **RF002**: O sistema deve permitir login com email institucional para funcionários
- **RF003**: O sistema deve implementar diferentes níveis de acesso (admin, bibliotecário, usuário)
- **RF004**: O sistema deve permitir recuperação de senha via email

### 1.2 Módulo de Gestão de Acervo
- **RF005**: O sistema deve permitir cadastrar novos livros (apenas administradores)
- **RF006**: O sistema deve permitir editar informações dos livros
- **RF007**: O sistema deve permitir exclusão lógica de livros
- **RF008**: O sistema deve permitir busca de livros por título, autor, ISBN ou assunto
- **RF009**: O sistema deve exibir status de disponibilidade do livro em tempo real

### 1.3 Módulo de Empréstimos e Devoluções
- **RF010**: O sistema deve registrar empréstimos de livros
- **RF011**: O sistema deve calcular data de devolução automaticamente (15 dias úteis)
- **RF012**: O sistema deve permitir renovação de empréstimo (máximo 2 renovações)
- **RF013**: O sistema deve registrar devoluções e calcular multas por atraso
- **RF014**: O sistema deve bloquear empréstimos para usuários com multas pendentes

### 1.4 Módulo de Reservas
- **RF015**: O sistema deve permitir reserva de livros indisponíveis
- **RF016**: O sistema deve notificar usuários quando livro reservado estiver disponível
- **RF017**: O sistema deve cancelar reservas após 48 horas de disponibilidade

### 1.5 Módulo de Relatórios
- **RF018**: O sistema deve gerar relatório de livros mais emprestados
- **RF019**: O sistema deve gerar relatório de usuários com mais empréstimos
- **RF020**: O sistema deve gerar relatório de multas em aberto

## 2. Requisitos Não-Funcionais (RNF)

### 2.1 Desempenho
- **RNF001**: O sistema deve suportar até 1000 usuários concorrentes
- **RNF002**: As consultas de busca devem retornar resultados em até 3 segundos
- **RNF003**: O tempo de resposta das operações CRUD deve ser inferior a 2 segundos

### 2.2 Segurança
- **RNF004**: Todas as senhas devem ser armazenadas usando hash bcrypt
- **RNF005**: O sistema deve implementar proteção contra ataques CSRF e XSS
- **RNF006**: A sessão do usuário deve expirar após 30 minutos de inatividade
- **RNF007**: Todas as comunicações devem usar HTTPS

### 2.3 Usabilidade
- **RNF008**: A interface deve ser responsiva e funcionar em dispositivos móveis
- **RNF009**: O sistema deve seguir princípios de WCAG 2.1 AA para acessibilidade
- **RNF010**: Curva de aprendizado não deve ultrapassar 15 minutos para usuários básicos

### 2.4 Confiabilidade
- **RNF011**: O sistema deve manter disponibilidade de 99.5% (SLA)
- **RNF012**: Backup automático deve ser executado diariamente
- **RNF013**: Em caso de falha, o sistema deve recuperar dados das últimas 4 horas

### 2.5 Compatibilidade
- **RNF014**: O sistema deve ser compatível com Chrome, Firefox, Safari e Edge (últimas 2 versões)
- **RNF015**: O sistema deve funcionar em dispositivos com resolução mínima de 320px

## 3. Regras de Negócio

### 3.1 Empréstimos
- **RN001**: Usuários de graduação podem emprestar até 3 livros simultaneamente
- **RN002**: Pós-graduandos podem emprestar até 5 livros simultaneamente
- **RN003**: Professores podem emprestar até 7 livros simultaneamente
- **RN004**: O prazo padrão de empréstimo é de 15 dias úteis para todos os usuários
- **RN005**: Livros raros ou de referência não podem ser emprestados

### 3.2 Multas
- **RN006**: Multa por atraso: R$ 2,00 por dia por livro
- **RN007**: Multa máxima por livro: R$ 40,00
- **RN008**: Usuários com multa superior a R$ 20,00 não podem realizar novos empréstimos
- **RN009**: Multas podem ser pagas na biblioteca ou online via sistema de pagamento integrado

### 3.3 Reservas
- **RN010**: Usuário pode ter até 2 reservas simultâneas
- **RN011**: Reserva expira após 48 horas da notificação de disponibilidade
- **RN012**: Livro reservado fica bloqueado para o usuário por 48 horas

### 3.4 Renovações
- **RN013**: Empréstimo pode ser renovado até 2 vezes, se não houver reservas
- **RN014**: Renovação deve ser solicitada até 2 dias antes do vencimento
- **RN015**: Não é permitida renovação se o usuário tem multas pendentes

## 4. Histórias de Usuário

### 4.1 Como Usuário da Biblioteca...
**HU001**: Como aluno, quero buscar livros por título ou autor para encontrar material de estudo rapidamente

**Critérios de Aceitação**:
- [ ] Campo de busca visível na página inicial
- [ ] Busca retorna resultados em até 3 segundos
- [ ] Resultados mostram título, autor, ano e disponibilidade
- [ ] É possível filtrar resultados por disponibilidade

**HU002**: Como aluno, quero renovar empréstimos online para evitar deslocamento até a biblioteca

**Critérios de Aceitação**:
- [ ] Botão de renovação visível na lista de empréstimos ativos
- [ ] Sistema valida se renovação é permitida (sem reservas, dentro do limite)
- [ ] Data de devolução é atualizada automaticamente
- [ ] Usuário recebe confirmação da renovação

### 4.2 Como Bibliotecário...
**HU003**: Como bibliotecário, quero registrar empréstimos rapidamente scanendo código do livro e matrícula do aluno para agilizar o atendimento

**Critérios de Aceitação**:
- [ ] Interface otimizada para leitor de código de barras
- [ ] Sistema valida se usuário pode realizar empréstimo
- [ ] Comprovante de empréstimo é gerado automaticamente
- [ ] Data de devolução é calculada automaticamente

**HU004**: Como bibliotecário, quero gerar relatórios de livros mais emprestados para auxiliar na gestão do acervo

**Critérios de Aceitação**:
- [ ] Relatório pode ser filtrado por período
- [ ] Dados são exportáveis em CSV e PDF
- [ ] Relatório mostra ranking dos 20 livros mais emprestados
- [ ] Inclui estatísticas de uso por departamento

### 4.3 Como Administrador...
**HU005**: Como administrador, quero cadastrar novos livros com todas as informações necessárias para manter o acervo atualizado

**Critérios de Aceitação**:
- [ ] Formulário com campos obrigatórios: ISBN, título, autor, editora, ano
- [ ] Validação de ISBN
- [ ] Upload de imagem da capa
- [ ] Confirmação de cadastro bem-sucedido

## 5. Perfis de Usuários

### 5.1 Aluno de Graduação
- **Descrição**: Estudante regularmente matriculado em curso de graduação
- **Permissões**:
  - Consultar acervo
  - Realizar empréstimos (até 3 livros)
  - Renovar empréstimos (até 2 vezes)
  - Reservar livros (até 2 reservas)
  - Visualizar seu histórico
- **Acesso**: Interface web pública

### 5.2 Aluno de Pós-Graduação
- **Descrição**: Estudante de mestrado ou doutorado
- **Permissões**:
  - Todas as permissões do aluno de graduação
  - Limite de 5 livros simultâneos
  - Acesso a livros restritos da pós-graduação
- **Acesso**: Interface web pública com verificação de vínculo

### 5.3 Professor
- **Descrição**: Corpo docente da universidade
- **Permissões**:
  - Todas as permissões do aluno de pós-graduação
  - Limite de 7 livros simultâneos
  - Prazo estendido para livros técnicos (30 dias)
  - Acesso a relatórios de uso por disciplina
- **Acesso**: Interface web com perfil professor

### 5.4 Bibliotecário
- **Descrição**: Funcionário responsável pelo atendimento na biblioteca
- **Permissões**:
  - Todas as permissões de consulta
  - Registrar empréstimos e devoluções
  - Aplicar multas manualmente
  - Cadastrar usuários
  - Gerar relatórios operacionais
- **Acesso**: Interface administrativa

### 5.5 Administrador do Sistema
- **Descrição**: Responsável pela gestão completa do sistema
- **Permissões**:
  - Todas as permissões do bibliotecário
  - Cadastrar e editar livros
  - Gerenciar usuários e permissões
  - Configurar parâmetros do sistema
  - Acessar todos os relatórios
  - Backup e manutenção do sistema
- **Acesso**: Interface administrativa completa

---

**Versão do Documento**: 1.0  
**Última Atualização**: 25/11/2024  
**Próxima Revisão**: 25/12/2024
