# 🗑️ Smart Waste Management System (SWMS)

## 💡 Overview  
O Smart Waste Management System é uma solução de Cidades Inteligentes que utiliza sistemas embarcados para monitorar e controlar o nível de resíduos urbanos.  
O projeto faz uso de sensores e atuadores conectados via MQTT, permitindo monitoramento em tempo real, controle automático e notificações de emergência.

---

## 💡 Ideia do Projeto 

O projeto Smart Waste Management System (SWMS) é uma solução de Cidades Inteligentes voltada à gestão automatizada de resíduos urbanos.
A proposta é monitorar, em tempo real, o nível de preenchimento de lixeiras inteligentes espalhadas pela cidade e otimizar o processo de coleta, reduzindo custos e evitando transbordamentos.
O sistema será composto por duas estações embarcadas simuladas (ESP32 ou Arduino):

- Lixeira Inteligente 1 (Sensor de nível ultrassônico + sensor de gás + atuador LED de alerta)
- Lixeira Inteligente 2 (Sensor de temperatura + sensor de peso + atuador servo para tampa automática)

As estações enviam dados via MQTT para um broker central.
Um servidor Node-RED atuará como painel de controle e interface com o banco de dados (simulado via SQLite ou Firebase).
O dashboard exibirá níveis de lixo, status de temperatura/gases, histórico e alarmes (com notificações configuráveis).

---

# ⚙️ Tecnologias Utilizadas  
- ESP32 (ou Arduino UNO) – Dispositivos embarcados simulados no Wokwi  
- Sensores:  
  - Ultrassônico (nível de preenchimento)  
  - MQ-2 (gases)  
  - DHT22 (temperatura e umidade)  
  - Célula de carga (peso)  
- Atuadores:  
  - Servo motor (abertura da tampa)  
  - LED (alerta de emergência)  
- Comunicação: MQTT via broker.hivemq.com  
- Dashboard: Node-RED  
- Banco de Dados: SQLite ou Firebase (armazenamento de leituras e alertas)  
- Notificações: Alerta configurável para temperatura, gás ou nível máximo  

# 🧩 Arquitetura do Sistema  
A[Lixeira 1 - ESP32] -->|MQTT| B(Broker)  
C[Lixeira 2 - ESP32] -->|MQTT| B  
B --> D[Node-RED Dashboard]  
D --> E[(SQLite DB)]  
D --> F[Alerta / Telegram / E-mail]  

---

# 🧠 Funcionalidades  
- Envio periódico dos dados dos sensores via MQTT  
- Controle automático da tampa (servo) quando a lixeira enche  
- Alerta visual (LED) e notificação via Node-RED em caso de emergência  
- Dashboard em Node-RED com gráficos de temperatura, nível e estado das lixeiras  
- Histórico armazenado no banco de dados  
- Configuração de limites de alerta personalizáveis  

---

# 🧪 Simulação  
Simulações realizadas no Wokwi com dois dispositivos ESP32.  
Cada dispositivo publica em tópicos MQTT distintos:  

| Dispositivo | Tópico MQTT | Sensores/Atuadores |  
|--------------|-------------|--------------------|  
| Lixeira 1 | swms/lixeira1/data | Ultrassônico, MQ-2, LED |  
| Lixeira 2 | swms/lixeira2/data | DHT22, Célula de carga, Servo |  

---

# 🧰 Estrutura do Repositório  
smart-waste-mqtt/  
├── devices/  
│   ├── lixeira1/  
│   │   └── main.py  
│   └── lixeira2/  
│       └── main.py  
├── node-red/  
│   └── flow.json  
├── database/  
│   ├── create_db.py  
│   └── queries.sql  
├── docs/  
│   ├── diagram.png  
│   └── report.md  
└── README.txt  

---

# 👥 EQUIPE  

| Nome | E-mail | Função |  
|------|---------|--------|  
| **Juliana Ballin Lima** | jbl.snf23@uea.edu.br | Banco de Dados, MQTT e Node-Red |  
| **Lucas Carvalho Dos Santos** | lcds.snf23@uea.edu.br | Hardware e Circuito |  
| **Ana Beatriz Maciel Nunes** | abmn.snf23@uea.edu.br | Node-RED e Conexão |  
| **Fernando Luiz Da Silva Freire** | fldsf.snf23@uea.edu.br | Dashboard e Visualização |  

---

# 👩‍💻 DISTRIBUIÇÃO DAS ATIVIDADES  

## 🔧 Atividade 1 – Hardware e Circuito  
**Responsável:** Lucas Carvalho Dos Santos <lcds.snf23@uea.edu.br>  

- Montagem do circuito eletrônico das lixeiras no **Wokwi**  
- Programação dos sensores e atuadores:  
  - Ultrassônico para medição de nível de lixo  
  - MQ-2 para detecção de gases  
  - DHT22 para temperatura e umidade  
  - Célula de carga para medição de peso  
  - Servo motor para tampa automática  
  - LED para alerta visual  
- Testes de comunicação serial e calibração dos sensores  
- Simulação dos dois dispositivos embarcados (ESP32 1 e ESP32 2)  
- Organização dos códigos no diretório `devices/`  

---

## 💾 Atividade 2 – Banco de Dados e MQTT  
**Responsável:** Juliana Ballin Lima <jbl.snf23@uea.edu.br> 

- Criação e configuração dos tópicos MQTT:  
  - swms/lixeira1/data  
  - swms/lixeira2/data  
- Desenvolvimento da comunicação MQTT com o **broker.hivemq.com**  
- Integração dos dispositivos ao fluxo Node-RED via MQTT  
- Criação do banco de dados **SQLite** com as tabelas:  
  - `leituras` (dados de sensores)  
  - `alertas` (eventos críticos)  
- Scripts em Python para:  
  - Inserção automática dos dados  
  - Consultas por período ou sensor  
- Testes de envio e recebimento de mensagens MQTT  

---

## 🌐 Atividade 3 – Node-RED e Conexão  
**Responsável:** Ana Beatriz Maciel Nunes <abmn.snf23@uea.edu.br>  

- Configuração do ambiente Node-RED  
- Importação dos fluxos de leitura via MQTT  
- Integração com o banco de dados (SQLite)  
- Criação do fluxo de armazenamento de dados e atualização periódica  
- Configuração de alarmes e envio de notificações (som, LED, ou mensagem)  
- Testes de conexão e estabilidade entre MQTT e Node-RED  

---

## 📊 Atividade 4 – Dashboard e Visualização  
**Responsável:** Fernando Luiz Da Silva Freire <fldsf.snf23@uea.edu.br>  

- Criação da interface visual no Node-RED Dashboard  
- Exibição em tempo real dos valores dos sensores:  
  - Nível, temperatura, gases e peso  
- Implementação de indicadores visuais (barras, gráficos e status coloridos)  
- Adição de alarmes configuráveis pelo usuário  
- Exibição de dados históricos (últimas 24h, 7 dias, etc.)  
- Design responsivo e intuitivo para exibição em tela cheia  

---

# 🧾 Cronograma  

| Data | Entrega |  
|------|----------|  
| 20–22/10 | Dúvidas e definição do escopo |  
| 29/10–03/11 | Implementação do sistema (código, dashboard e banco) |  
| 05/11 | Apresentação e demonstração do projeto |  

---

# 🧠 Contexto Acadêmico  
Trabalho Final (P2) da disciplina **Sistemas Embarcados**  
Tema: **Cidades Inteligentes e IoT – Automação de Gestão de Resíduos Urbanos**  

---

# 📦 Requisitos do Projeto  
- 2 dispositivos embarcados simulados  
- 4 sensores e 2 atuadores diferentes  
- Comunicação via MQTT  
- Controle automático (tampa automática da lixeira)  
- Dashboard de monitoramento e interação (Node-RED)  
- Banco de dados para armazenamento e consulta  
- Alertas configuráveis para situações de emergência  
- Simulação com Wokwi  
- Criatividade e integração avançada  

---

# 📘 Nome e Descrição do Repositório (GitHub)  
**Repositório:** smart-waste-mqtt  
**Descrição:**  
Smart Waste Management System – Projeto acadêmico com dispositivos embarcados, MQTT, Node-RED e dashboard IoT.  
Simulação em Wokwi de lixeiras inteligentes com sensores de nível, gás, temperatura e peso, além de atuadores automáticos e alarmes.  

---

# 🧾 Licença  
Este projeto é de uso acadêmico e educacional, desenvolvido como parte do **Trabalho Final – P2** da disciplina de **Sistemas Embarcados**.
