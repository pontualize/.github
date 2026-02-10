# Sistema de Ponto e Controle de RH 🕐

Este repositório contém workflows, templates e automações para gerenciar o controle de ponto e processos de RH da organização Pontualize.

## 📋 Índice

- [Funcionalidades](#funcionalidades)
- [Como Usar](#como-usar)
  - [Registrar Ponto](#registrar-ponto)
  - [Solicitar Férias](#solicitar-férias)
  - [Solicitar Horas Extras](#solicitar-horas-extras)
  - [Solicitar Correção de Ponto](#solicitar-correção-de-ponto)
- [Workflows Disponíveis](#workflows-disponíveis)
- [Relatórios](#relatórios)
- [Estrutura do Repositório](#estrutura-do-repositório)

## ✨ Funcionalidades

### 🟢 Registro de Ponto Diário
- Registro de entrada, saída para almoço, retorno do almoço e saída
- Armazenamento automático em arquivos markdown datados
- Controle de horários com timestamp preciso
- Possibilidade de adicionar observações

### 📊 Relatórios Automáticos
- Geração automática de relatórios mensais
- Consolidação de registros por colaborador
- Estatísticas de frequência
- Criação automática de issues com resumos

### 🔔 Lembretes Automáticos
- Lembretes nos horários de registro (9h, 12h, 14h, 18h)
- Instruções de como registrar o ponto
- Notificações via discussions ou issues

### 📝 Templates de Solicitação
- Solicitação de férias
- Solicitação de horas extras
- Correção de registros de ponto

## 🚀 Como Usar

### Registrar Ponto

1. Acesse a aba **Actions** do repositório
2. Selecione o workflow **"Registro de Ponto Diário"**
3. Clique em **"Run workflow"**
4. Preencha os campos:
   - **Ação**: Escolha entre:
     - `entrada` - Registro de entrada
     - `saida-almoco` - Saída para almoço
     - `retorno-almoco` - Retorno do almoço
     - `saida` - Saída final
   - **Observação** (opcional): Adicione informações relevantes
5. Clique em **"Run workflow"** para confirmar

O sistema criará automaticamente um registro no arquivo `registros-ponto/YYYY-MM-DD.md` com:
- Horário exato do registro
- Tipo de registro (entrada/saída)
- Nome do usuário
- Observações (se houver)

### Solicitar Férias

1. Vá para a aba **Issues**
2. Clique em **"New issue"**
3. Selecione o template **"Solicitação de Férias"**
4. Preencha todos os campos obrigatórios:
   - Nome do colaborador
   - Data de início e término
   - Total de dias
   - Tipo de férias
5. Marque as confirmações
6. Clique em **"Submit new issue"**

A solicitação será revisada pelo gestor e RH.

### Solicitar Horas Extras

1. Vá para a aba **Issues**
2. Clique em **"New issue"**
3. Selecione o template **"Solicitação de Horas Extras"**
4. Preencha todos os campos:
   - Nome do colaborador
   - Data e horários
   - Total de horas
   - Tipo de hora extra
   - Justificativa
5. Marque as confirmações
6. Clique em **"Submit new issue"**

### Solicitar Correção de Ponto

1. Vá para a aba **Issues**
2. Clique em **"New issue"**
3. Selecione o template **"Correção de Ponto"**
4. Preencha os campos:
   - Data do registro
   - Tipo de registro a corrigir
   - Horário registrado e horário correto
   - Motivo da correção
   - Justificativa detalhada
5. Anexe comprovantes se necessário
6. Clique em **"Submit new issue"**

## 🔄 Workflows Disponíveis

### 1. Registro de Ponto Diário (`ponto-diario.yml`)
- **Trigger**: Manual (workflow_dispatch)
- **Função**: Registra ponto de entrada/saída
- **Output**: Arquivo markdown em `registros-ponto/`

### 2. Relatório de Frequência Mensal (`relatorio-mensal.yml`)
- **Trigger**: Automático (último dia do mês às 18h) ou Manual
- **Função**: Gera relatório consolidado do mês
- **Output**: 
  - Arquivo markdown em `relatorios-mensais/`
  - Issue com resumo do mês

### 3. Lembrete de Registro de Ponto (`lembrete-ponto.yml`)
- **Trigger**: Automático (9h, 12h, 14h, 18h - Seg-Sex)
- **Função**: Envia lembretes de registro
- **Output**: Discussion ou issue com instruções

## 📈 Relatórios

### Registros Diários
Os registros diários são armazenados em `registros-ponto/` no formato:
```
registros-ponto/
  ├── 2024-01-15.md
  ├── 2024-01-16.md
  └── ...
```

Cada arquivo contém:
- Data do registro
- Lista de todos os registros do dia
- Horários e tipos de registro
- Observações

### Relatórios Mensais
Os relatórios mensais são gerados em `relatorios-mensais/` no formato:
```
relatorios-mensais/
  ├── relatorio-2024-01.md
  ├── relatorio-2024-02.md
  └── ...
```

Cada relatório contém:
- Resumo de todos os registros do mês
- Estatísticas de frequência
- Lista de colaboradores
- Total de registros

## 🗂️ Estrutura do Repositório

```
.github/
├── ISSUE_TEMPLATE/
│   ├── config.yml                      # Configuração de templates
│   ├── solicitacao-ferias.yml          # Template de férias
│   ├── solicitacao-horas-extras.yml    # Template de horas extras
│   └── correcao-ponto.yml              # Template de correção
├── workflow-templates/
│   ├── ponto-diario.yml                # Template do workflow de ponto
│   ├── ponto-diario.properties.json
│   ├── relatorio-mensal.yml            # Template de relatório mensal
│   ├── relatorio-mensal.properties.json
│   ├── lembrete-ponto.yml              # Template de lembretes
│   └── lembrete-ponto.properties.json
└── pull_request_template.md            # Template de PR

registros-ponto/                         # Registros diários (criado automaticamente)
relatorios-mensais/                      # Relatórios mensais (criado automaticamente)
```

## 📱 Uso via GitHub Mobile

Você pode registrar seu ponto usando o aplicativo GitHub Mobile:

1. Abra o app GitHub Mobile
2. Navegue até o repositório
3. Acesse **Actions**
4. Selecione o workflow e execute
5. Preencha os campos necessários

## 🔒 Políticas e Permissões

- Apenas colaboradores autorizados podem executar workflows
- Correções de ponto precisam de aprovação do gestor
- Solicitações de férias e horas extras passam por revisão do RH
- Todos os registros são versionados e rastreáveis via Git

## 🆘 Suporte

Em caso de dúvidas ou problemas:
1. Consulte esta documentação
2. Abra uma discussão na aba Discussions
3. Entre em contato com o RH

## 📄 Licença

Este projeto é de uso interno da organização Pontualize.

---

**Última atualização**: 2024
**Versão**: 1.0.0