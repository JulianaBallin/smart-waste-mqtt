# 🗑️ Smart Waste Management System (SWMS)

## 💡 Overview
O Smart Waste Management System é uma solução de Cidades Inteligentes que utiliza sistemas embarcados para monitorar e controlar o nível de resíduos urbanos.
O projeto faz uso de sensores e atuadores conectados via MQTT, permitindo monitoramento em tempo real, controle automático e notificações de emergência.

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

# 🧠 Funcionalidades
- Envio periódico dos dados dos sensores via MQTT
- Controle automático da tampa (servo) quando a lixeira enche
- Alerta visual (LED) e notificação via Node-RED em caso de emergência
- Dashboard em Node-RED com gráficos de temperatura, nível e estado das lixeiras
- Histórico armazenado no banco de dados
- Configuração de limites de alerta personalizáveis

# 🧪 Simulação
Simulações realizadas no Wokwi com dois dispositivos ESP32.
Cada dispositivo publica em tópicos MQTT distintos:

| Dispositivo | Tópico MQTT | Sensores/Atuadores |
|--------------|-------------|--------------------|
| Lixeira 1 | swms/lixeira1/data | Ultrassônico, MQ-2, LED |
| Lixeira 2 | swms/lixeira2/data | DHT22, Célula de carga, Servo |

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

# 🧑‍🤝‍🧑 Equipe e Divisão de Tarefas

| Integrante | Função | Responsabilidades |
|-------------|--------|------------------|
| Aluno 1 – Líder / Back-end MQTT | Desenvolvimento da comunicação MQTT, tópicos, e integração entre dispositivos. |
| Aluno 2 – Dispositivos e Sensores (Wokwi) | Programação dos ESP32 (leitura dos sensores e acionamento de atuadores). |
| Aluno 3 – Dashboard Node-RED e Notificações | Criação do painel de monitoramento, alertas e integração com banco de dados. |
| Aluno 4 – Banco de Dados e Documentação | Estruturação do banco, histórico de dados, README e relatório final. |

# 👩‍💻 Distribuição das Tarefas (detalhada)

## Aluno 1 – Líder técnico / MQTT Broker Integration
- Configurar tópicos MQTT (swms/lixeira1/data, swms/lixeira2/data)
- Programar assinaturas e publicações
- Implementar script central de leitura no Node-RED
- Testar envio de pacotes simulados

## Aluno 2 – Programação dos Dispositivos (Wokwi)
- Programar ESP32 1 (Ultrassônico + MQ-2 + LED)
- Programar ESP32 2 (DHT22 + Célula de carga + Servo)
- Testar leituras periódicas e comunicação com o broker
- Enviar JSONs formatados com dados dos sensores

## Aluno 3 – Dashboard e Alerta
- Criar interface no Node-RED com gráficos e botões
- Integrar dados MQTT com visualização em tempo real
- Criar lógica de alerta configurável (limite temperatura, gás, nível)
- Integrar com Telegram ou notificação sonora/visual

## Aluno 4 – Banco de Dados e Documentação
- Criar banco SQLite/Firebase para armazenar leituras
- Implementar scripts de inserção e consulta
- Documentar o projeto (README + relatório final)
- Elaborar diagrama de arquitetura e instruções de execução

# 🧾 Cronograma

| Data | Entrega |
|------|----------|
| 20–22/10 | Dúvidas e definição do escopo |
| 29/10–03/11 | Implementação do sistema (código, dashboard e banco) |
| 05/11 | Apresentação e demonstração do projeto |

# 🧠 Contexto Acadêmico
Trabalho Final (P2) da disciplina Sistemas Embarcados.
Tema: Cidades Inteligentes e IoT – Automação de Gestão de Resíduos Urbanos.

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

# 📅 Cronograma Oficial da Disciplina
- 20/10 e 22/10: Tira-Dúvidas do Projeto (sem frequência)
- 29/10 e 03/11: Implementação do Projeto (com frequência)
- 05/11: Entregas com demonstração do projeto (com frequência)

# 📘 Nome e Descrição do Repositório (GitHub)
Repositório: smart-waste-mqtt
Descrição: Smart Waste Management System – Projeto acadêmico com dispositivos embarcados, MQTT, Node-RED e dashboard IoT.
Simulação em Wokwi de lixeiras inteligentes com sensores de nível, gás, temperatura e peso, além de atuadores automáticos e alarmes.

# 🧾 Licença
Este projeto é de uso acadêmico e educacional, desenvolvido como parte do Trabalho Final – P2 da disciplina de Sistemas Embarcados.
