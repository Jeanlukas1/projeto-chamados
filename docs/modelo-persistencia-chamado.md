# Modelo de Persistência — Chamado

## Entidade

A entidade Chamado representa uma solicitação de suporte registrada pela API e armazenada de forma persistente no banco de dados.

## Modelo simplificado

Chamado
- id: identificador único
- titulo: texto obrigatório
- descricao: texto obrigatório
- status: aberto | em_andamento | fechado
- criado_em: data e hora

## Campos

| Campo | Tipo conceitual | Regra |
|---|---|---|
| id | inteiro | Identificador único gerado pelo banco |
| titulo | texto | Obrigatório |
| descricao | texto | Obrigatório |
| status | texto | Obrigatório; valores permitidos: aberto, em_andamento e fechado |
| criado_em | data e hora | Gerado automaticamente no momento da criação |

## Regras de integridade

- id deve identificar unicamente cada chamado.
- titulo não pode ser nulo.
- descricao não pode ser nula.
- status não pode ser nulo.
- status deve aceitar somente os valores definidos pelo modelo.
- criado_em deve ser preenchido automaticamente.
- A geração do identificador e da data de criação será responsabilidade da camada de persistência.

## Correspondência com a API

O modelo de persistência será utilizado como base para a integração dos endpoints de chamados com o banco de dados.

A API existente possui campos adicionais relacionados ao contrato definido anteriormente, como prioridade. A integração com a persistência deverá considerar a compatibilidade entre o contrato atual da API e o modelo do banco, sem alterar o contrato nesta etapa.

## Decisão técnica

A modelagem da entidade é registrada separadamente da implementação da tabela e do acesso ao banco. Dessa forma, o modelo pode ser validado antes da criação do script SQL e da integração da API com a persistência.

A criação da estrutura física da tabela será realizada na etapa seguinte.
