# Pipeline de Dados com IoT e Docker

## Visão Geral
Este projeto cria um pipeline de dadospara processar leituras de temperatura de dispositivos IoT, armazenando-as em um banco de dados PostgreSQL utilizando Docker. Além disso, um dashboard interativo foi desenvolvido com Streamlit e Plotly para visualização dos dados.

## Tecnologias Utilizadas
- **Python**
- **PostgreSQL**
- **Docker**
- **SQLAlchemy**
- **Pandas**
- **Streamlit**
- **Plotly**
- **Git e GitHub**


## Estrutura do Projeto
```
├── temperature_readings.csv   # Conjunto de dados IoT (Kaggle)
├── pipeline.py                # Código para processar e inserir os dados
├── dashboard.py               # Dashboard interativo com Streamlit
├── Dockerfile                 # Configuração do contêiner
├── README.md                  # Documentação do projeto
```

---

## Configuração e Execução

### **Clonar o repositório**
```bash
git clone https://github.com/seu_usuario/pipeline_iot.git
cd pipeline_iot
```

### **Configurar e executar o banco de dados PostgreSQL no Docker**
```bash
docker run --name postgres-iot -e POSTGRES_PASSWORD=sua_senha -p 5432:5432 -d postgres
```

### **Criar o banco de dados e a tabela**
```sql
CREATE DATABASE iot_data;
\c iot_data;

CREATE TABLE temperature_readings (
    id SERIAL PRIMARY KEY,
    device_id VARCHAR(50),
    temperature FLOAT,
    timestamp TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

### **Instalar as dependências do projeto**
```bash
pip install pandas psycopg2-binary sqlalchemy streamlit plotly
```

### **Processar e inserir os dados IoT no banco**
```bash
python pipeline.py
```

### **Executar o dashboard interativo**
```bash
streamlit run dashboard.py
```

## 📊 Visualização dos Dados
### O dashboard interativo exibe:
Média de temperatura por dispositivo
Leituras de temperatura por hora
Temperaturas máximas e mínimas por dia

---

## Consultas SQL Utilizadas
**view SQL** criada para análise dos dados:
```sql
CREATE VIEW avg_temp_por_dispositivo AS
SELECT device_id, AVG(temperature) as avg_temp
FROM temperature_readings
GROUP BY device_id;
```

## Publicação no GitHub
Para enviar o projeto ao GitHub:
```bash
git init
git add .
git commit -m "Projeto inicial: Pipeline de Dados IoT"
git remote add origin URL_DO_SEU_REPOSITORIO
git push -u origin main
```

## Conclusão
Este projeto demonstra a criação de um pipeline de dados completo, integrando **IoT, PostgreSQL, Docker e Streamlit**. O dashboard interativo facilita a análise dos dados coletados.
