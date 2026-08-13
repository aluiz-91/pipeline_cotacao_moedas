# 📈 Pipeline de Ingestão e Monitoramento de Cotações (ETL)

Este é um projeto prático de Engenharia de Dados focado no conceito de **ETL (Extract, Transform, Load)**. O script automatiza a extração diária de moedas estrangeiras em tempo real, gerencia o armazenamento persistente em um banco de dados relacional e entrega relatórios estruturados para análise de negócios.

## 🛠️ Arquitetura e Tecnologias
* **Python 3**: Linguagem principal utilizada para construir o pipeline de automação.
* **Requests (API REST)**: Consumo e captura dos dados financeiros brutos do mercado da *AwesomeAPI*.
* **SQLite3 (SQL)**: Banco de dados relacional local integrado para a persistência histórica das cotações.
* **Pandas**: Framework de manipulação analítica usado para converter dados do banco em tabelas organizadas (`DataFrames`) e exportação final.

## 🚀 Os 8 Passos Lógicos do Pipeline
1. **Extração**: Captura a cotação ao vivo do Dólar e Euro com tratamentos de erros de rede (`try/except`).
2. **Conexão**: Abre os canais de comunicação com o arquivo local do banco `meu_banco.db`.
3. **Estrutura (DDL)**: Cria a tabela de registros utilizando a cláusula de segurança `IF NOT EXISTS`.
4. **Inserção (DML)**: Salva as variáveis reais coletadas através de *placeholders* seguros `(?, ?, ?)`.
5. **Persistência**: Executa o `commit` forçando o salvamento permanente dos dados no disco rígido.
6. **Processamento**: O Pandas lê o histórico direto do SQLite convertendo-o em uma planilha virtual na memória.
7. **Carga (Delivery)**: Exibe a tabela organizada no terminal e gera o arquivo físico `.csv` legível no Excel.
8. **Limpeza**: Encerra as conexões ativas do banco de dados para evitar corrupção de arquivos.

## 📦 Como Executar o Projeto
1. Clone o repositório para sua máquina.
2. Certifique-se de instalar as dependências necessárias executando no terminal:
   ```bash
   python -m pip install pandas requests
   ```
3. Execute o script principal:
   ```bash
   python meu_banco.py
   ```
4. Verifique os dados inseridos e abra o arquivo `historico_cotacoes.csv` gerado de forma automática.
