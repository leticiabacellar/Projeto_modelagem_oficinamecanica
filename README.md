# Projeto: Modelagem Conceitual para Oficina Mecânica

## Objetivo
Criar um esquema conceitual para o gerenciamento de ordens de serviço em uma oficina mecânica, com base na narrativa fornecida. O esquema abrange todas as entidades, relacionamentos e atributos necessários para representar o contexto do sistema.

---

## Contexto
A narrativa descreve o seguinte:

1. **Clientes** levam seus **veículos** para conserto ou revisão periódica.
2. Cada **veículo** é designado a uma **equipe de mecânicos**, que:
   - Identifica os serviços a serem executados.
   - Preenche uma **ordem de serviço (OS)** com a data de entrega.
3. A partir da **OS**:
   - Calcula-se o valor de cada serviço, consultando uma tabela de referência de mão-de-obra.
   - O valor das peças também é incluído na OS.
4. O cliente autoriza a execução dos serviços.
5. A mesma equipe avalia e executa os serviços.
6. Os **mecânicos** possuem:
   - Código.
   - Nome.
   - Endereço.
   - Especialidade.
7. Cada **OS** possui:
   - Número.
   - Data de emissão.
   - Valor.
   - Status.
   - Data de conclusão dos trabalhos.

---

## Esquema Conceitual

### Entidades e Atributos

1. **Cliente**:
   - ID (Chave Primária)
   - Nome
   - CPF/CNPJ
   - Telefone
   - Endereço

2. **Veículo**:
   - Placa (Chave Primária)
   - Modelo
   - Marca
   - Ano
   - Cliente_ID (Chave Estrangeira para Cliente)

3. **Mecânico**:
   - ID (Chave Primária)
   - Nome
   - Endereço
   - Especialidade

4. **Equipe**:
   - ID (Chave Primária)
   - Nome da Equipe

5. **Equipe_Mecânico** (Relacionamento entre Equipe e Mecânico):
   - Equipe_ID (Chave Estrangeira para Equipe)
   - Mecânico_ID (Chave Estrangeira para Mecânico)

6. **Ordem de Serviço (OS)**:
   - Número (Chave Primária)
   - Data de Emissão
   - Valor Total
   - Status
   - Data de Conclusão
   - Veículo_Placa (Chave Estrangeira para Veículo)
   - Equipe_ID (Chave Estrangeira para Equipe)

7. **Serviço**:
   - ID (Chave Primária)
   - Descrição
   - Valor Mão-de-Obra (Consultado na tabela de referência)

8. **Peça**:
   - ID (Chave Primária)
   - Nome
   - Valor

9. **OS_Serviço** (Relacionamento entre OS e Serviço):
   - OS_Número (Chave Estrangeira para OS)
   - Serviço_ID (Chave Estrangeira para Serviço)

10. **OS_Peça** (Relacionamento entre OS e Peça):
    - OS_Número (Chave Estrangeira para OS)
    - Peça_ID (Chave Estrangeira para Peça)

---

## Descrição do Esquema Conceitual
O esquema conceitual é composto por entidades que representam os principais elementos do contexto de uma oficina mecânica, como clientes, veículos, mecânicos, equipes, ordens de serviço, peças e serviços. Os relacionamentos foram modelados para garantir a integridade dos dados e permitir consultas eficientes sobre as operações da oficina.
