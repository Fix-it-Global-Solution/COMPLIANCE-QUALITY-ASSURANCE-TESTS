# Fix-It — Compliance, Quality Assurance & Tests
> **Global Solution 2026/2** • FIAP • Turma **2TDSPF**  
> Gestão de Qualidade, Planejamento Ágil e Testes de Software para Plataforma de Zeladoria Urbana.

---

## 👥 Integrantes da Equipe

| Nome Completo | RM | Turma |
| :--- | :---: | :---: |
| **Gabriel Sbrana Campos** | 565849 | 2TDSPF |
| **Moisés Waidemann Molinillo** | 563719 | 2TDSPF |
| **Richard Freitas** | 566127 | 2TDSPF |
| **Thiago Rodrigues da Mota** | 563650 | 2TDSPF |

---

## 🎯 Objetivo da Disciplina

Implementar o planejamento ágil e a garantia de qualidade de ponta a ponta da solução **Fix-It** utilizando o ecossistema **Azure DevOps**:
1. **Estruturação de Backlog de Produto:** Mapeamento hierárquico com Epics, Features e PBIs orientados ao usuário (*User Stories*).
2. **Critérios de Aceite em BDD:** Especificação formal de requisitos no formato *Dado-Quando-Então* (*Given-When-Then*).
3. **Casos de Teste Funcionais (Test Cases):** Cobertura caixa-preta (cenários positivos e negativos) com rastreabilidade total.
4. **Execução e Auditoria:** Operação com Test Runner e relatórios analíticos de homologação.

---

## 🔗 Link Oficial do Projeto

- **Azure DevOps (Boards & Test Plans):**  
  [https://dev.azure.com/RM565849/Fix-It%20-%20Global%20Solution](https://dev.azure.com/RM565849/Fix-It%20-%20Global%20Solution)  
  *(Acesso com perfil **Project Administrator** concedido ao professor avaliador).*

---

## 📋 Estrutura do Backlog Ágil (Azure Boards)

O backlog foi organizado em três níveis de granularidade:

- **Epic 26: Gestão de Incidentes Urbanos**
  - **Feature 34:** Registro Georreferenciado de Anomalias Urbanas
    - *PBI 35:* Captura de Foto com GPS Automático
    - *PBI 36:* Formulário de Categorização e Relato de Danos
  - **Feature 37:** Acompanhamento Cidadão e Histórico
    - *PBI 38:* Listagem de Chamados do Munícipe
    - *PBI 39:* Cancelamento de Chamado Pendente de Vistoria
- **Epic 27: Triagem Inteligente e Despacho Público**
  - **Feature 40:** Triagem Automatizada por Inteligência Artificial
    - *PBI 42:* Classificação de Severidade por Visão Computacional
    - *PBI 43:* Geração de Parecer Preliminar e Roteamento via LLM
  - **Feature 41:** Despacho e Gestão de Ordens de Serviço
    - *PBI 44:* Transição de Status da Ordem de Serviço
    - *PBI 45:* Atribuição de Equipe de Campo
- **Epic 28: Segurança e Autenticação de Usuários**
  - **Feature 46:** Controle de Acesso Baseado em Perfis (RBAC)
    - *PBI 47:* Autenticação via Token JWT para Munícipes
    - *PBI 48:* Bloqueio de Rotas Administrativas para Não-Gestores

---

## 🧪 Matriz de Testes Funcionais (Test Cases)

Foram documentados 10 Casos de Teste completos (com Sumário, Pré-condições, Inputs, Outputs e Passos detalhados de Ação/Resultado Esperado):

| ID | Test Case | Feature Pai | Tipo | Foco de Validação |
| :---: | :--- | :---: | :---: | :--- |
| **TC01** | Registro de chamado com foto e GPS válido | Feature 34 | Positivo | Submissão íntegra de ocorrência com coordenadas reais (HTTP 201). |
| **TC02** | Tentativa de envio sem GPS | Feature 34 | Negativo | Bloqueio de chamado anônimo/sem coordenadas (HTTP 400). |
| **TC03** | Cancelamento de chamado pendente | Feature 37 | Positivo | Munícipe cancela chamado com status "Aberto" (HTTP 200). |
| **TC04** | Cancelamento indevido em execução | Feature 37 | Negativo | Bloqueio de cancelamento após equipe técnica despachada (HTTP 409). |
| **TC05** | Inferência de dano viário com severidade | Feature 40 | Positivo | Modelo IA detecta anomalia viária com confiança ≥ 80% (Severidade Crítica). |
| **TC06** | Envio de imagem inválida/ruído | Feature 40 | Negativo | Fallback resiliente para "Revisão Manual" em fotos sem dano viário. |
| **TC07** | Despacho de OS com vinculação de equipe | Feature 41 | Positivo | Transição para "Em Execução" com persistência relacional da equipe. |
| **TC08** | Conclusão de OS sem foto comprobatória | Feature 41 | Negativo | Bloqueio de auditoria pública ao tentar concluir reparo sem imagem (HTTP 422). |
| **TC09** | Autenticação com emissão de token JWT | Feature 46 | Positivo | Login de munícipe com retorno de Bearer Token e role `ROLE_CIDADAO`. |
| **TC10** | Bloqueio de acesso a rota administrativa | Feature 46 | Negativo | Proteção perimetral com resposta imediata HTTP 403 Forbidden. |

---

## 📁 Estrutura dos Arquivos da Entrega

```text
├── README.md                           # Documentação resumida para o GitHub
├── Plano_de_Projeto_e_Testes_FixIt.pdf # Documento PDF oficial com prints das telas do Azure
└── identificacao.txt                   # Arquivo com RMs, integrantes e link do projeto
```

---

## 💻 Rastreabilidade e Execução

- **Rastreabilidade:** Consulta em árvore (*Tree of work items*) relacionando `Feature -> Test Case`.
- **Test Runner:** Execução manual de cada step com evidência de passagem (*Passed Steps*), validação de status HTTP e verificação das tabelas de auditoria do banco de dados.
