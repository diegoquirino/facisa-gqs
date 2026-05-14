# Disciplina: Segurança da Informação | Trabalho Prático — Descritivo do Sistema | Sistema 06 — IoT Industrial / OT (Tecnologia Operacional)

---

---

## 1. IDENTIFICAÇÃO DO SISTEMA

**Nome da Empresa:** SmartFactory Indústria 4.0 Ltda.

**Nome do Sistema:** SmartFactory Platform — Plataforma Integrada de Automação Industrial e IIoT

**Setor:** Manufatura Avançada / Indústria 4.0

**Porte:** Empresa de médio-grande porte com operações nacionais

**Ano de Fundação (Fictício):** 2018

**Localização:** Matriz em Campinas/SP, com plantas industriais em São Paulo, Minas Gerais, Rio Grande do Sul e Bahia

**Modelo de Atuação:** Fabricante de componentes eletrônicos de precisão e operador de plataforma IIoT (Industrial Internet of Things) para automação de manufatura

---

---

## 2. CONTEXTO DE NEGÓCIO DETALHADO

### 2.1. Missão e Visão

**Missão:** Transformar a manufatura brasileira através da digitalização inteligente, oferecendo soluções integradas de automação industrial que aumentem a produtividade, reduzam desperdícios e promovam a sustentabilidade operacional, conectando o chão de fábrica à inteligência de negócios em tempo real.

**Visão:** Ser reconhecida até 2030 como a principal referência nacional em soluções de Indústria 4.0, liderando a transformação digital do setor manufatureiro brasileiro através da convergência entre Tecnologia da Informação (IT) e Tecnologia Operacional (OT), com excelência em segurança cibernética industrial.

### 2.2. Modelo de Negócio

A SmartFactory opera em um modelo de negócio dual e integrado:

**a) Fabricante de Componentes Eletrônicos de Precisão:** Produz componentes eletrônicos de alta precisão para os setores automotivo, aeroespacial, médico-hospitalar e de energia. A produção é altamente automatizada, utilizando linhas de montagem robotizadas, sistemas de controle de qualidade baseados em visão computacional e processos de manufatura aditiva (impressão 3D industrial).

**b) Operador de Plataforma IIoT:** Desenvolveu e comercializa a "SmartFactory Platform", uma solução proprietária de automação industrial que integra sistemas SCADA (Supervisory Control and Data Acquisition), DCS (Distributed Control Systems), análise preditiva com inteligência artificial, digital twins e dashboards gerenciais em tempo real. A plataforma é oferecida tanto para uso interno quanto como solução SaaS (Software as a Service) para clientes industriais de médio e grande porte.

Este modelo dual cria uma sinergia única: a empresa utiliza sua própria plataforma em suas operações de manufatura, gerando casos de uso reais e aprimoramentos contínuos que são posteriormente comercializados para clientes externos. Essa abordagem "dogfooding" (usar o próprio produto) fortalece a credibilidade da solução no mercado e acelera ciclos de inovação.

### 2.3. Usuários e Stakeholders

O ecossistema da SmartFactory envolve múltiplos perfis de usuários com necessidades e níveis de acesso distintos:

**Usuários Internos:**

- **Operadores de Chão de Fábrica (150 usuários):** Interagem com interfaces HMI (Human-Machine Interface) para monitoramento de linhas de produção, ajustes de parâmetros operacionais e resposta a alarmes. Possuem acesso limitado a funções específicas de suas estações de trabalho.

- **Engenheiros de Processo (45 usuários):** Responsáveis pela otimização de processos produtivos, programação de PLCs (Programmable Logic Controllers), configuração de receitas de produção e análise de dados de qualidade. Requerem acesso privilegiado a sistemas de controle e historiadores de dados.

- **Técnicos de Manutenção (60 usuários):** Executam manutenção preventiva e corretiva em equipamentos, utilizando sistemas de manutenção preditiva baseados em IA para priorização de intervenções. Necessitam acesso a dados de sensores, históricos de falhas e documentação técnica.

- **Gestores de Produção (20 usuários):** Monitoram KPIs (Key Performance Indicators) de produção, eficiência energética, qualidade e OEE (Overall Equipment Effectiveness) através de dashboards executivos. Tomam decisões estratégicas baseadas em análises de tendências e previsões.

- **Equipe de TI/OT (25 usuários):** Administradores de sistemas, engenheiros de redes industriais, especialistas em segurança cibernética OT e desenvolvedores da plataforma IIoT. Possuem acesso administrativo completo e são responsáveis pela segurança e disponibilidade dos sistemas.

**Usuários Externos (Clientes Industriais):**

- **Clientes SaaS da Plataforma (80 empresas, ~500 usuários):** Indústrias de diversos setores que contratam a SmartFactory Platform como serviço. Cada cliente possui ambientes isolados (multi-tenancy) com dados segregados e níveis de customização variados.

- **Parceiros de Integração (15 empresas):** Integradores de sistemas que implementam e customizam a plataforma SmartFactory em clientes finais, requerendo acesso a APIs, documentação técnica e ambientes de desenvolvimento/homologação.

### 2.4. Escala de Operação

A SmartFactory opera em escala significativa, caracterizada pelos seguintes números:

**Infraestrutura Física:**
- 4 plantas industriais distribuídas geograficamente
- 12 linhas de produção automatizadas
- 850+ dispositivos IIoT conectados (sensores, atuadores, câmeras industriais)
- 120 PLCs (Programmable Logic Controllers) de diversos fabricantes
- 45 HMIs (Human-Machine Interfaces) distribuídas pelo chão de fábrica
- 8 sistemas SCADA/DCS centralizados
- 15 robôs industriais colaborativos (cobots)

**Volume de Dados:**
- 2,5 milhões de pontos de dados coletados por segundo
- 180 TB de dados históricos de processo armazenados
- 12 TB de novos dados gerados mensalmente
- Latência crítica < 100ms para sistemas de controle em tempo real
- Disponibilidade requerida: 99,9% (máximo 8,76 horas de downtime/ano)

**Operação Contínua:**
- Operação 24/7/365 em regime de turnos
- Processos críticos que não podem ser interrompidos sem perdas significativas
- Janelas de manutenção extremamente limitadas (geralmente durante paradas programadas anuais)

### 2.5. Convergência IT/OT: Desafio Central

O principal desafio estratégico da SmartFactory é a **convergência entre Tecnologia da Informação (IT) e Tecnologia Operacional (OT)**. Historicamente, esses dois mundos operavam de forma isolada:

**IT (Information Technology):**
- Prioridade: Confidencialidade, Integridade, Disponibilidade (nesta ordem)
- Ciclos de atualização frequentes
- Conectividade ampla e acesso remoto
- Foco em proteção de dados e privacidade

**OT (Operational Technology):**
- Prioridade: Disponibilidade, Integridade, Confidencialidade (nesta ordem)
- Sistemas legados com ciclos de vida de 15-25 anos
- Redes isoladas (air-gapped) historicamente
- Foco em segurança física e continuidade operacional

A Indústria 4.0 exige a integração desses mundos para viabilizar análises em tempo real, manutenção preditiva e otimização baseada em dados. No entanto, essa convergência cria novos vetores de ataque: vulnerabilidades de sistemas IT podem agora impactar diretamente processos físicos críticos, enquanto sistemas OT legados, projetados sem considerações de cibersegurança, tornam-se expostos a ameaças modernas.

A SmartFactory enfrenta este desafio através de uma arquitetura de segurança em camadas baseada no Purdue Model, com zonas de segurança bem definidas, firewalls industriais, segmentação de redes e monitoramento contínuo de tráfego OT. No entanto, a pressão por maior integração e acesso remoto (especialmente após a pandemia de COVID-19) continua tensionando os limites de segurança estabelecidos.

---

---

## 3. PRINCIPAIS FUNCIONALIDADES

A SmartFactory Platform oferece um conjunto integrado de funcionalidades que abrangem todo o ciclo de vida da manufatura inteligente:

### 3.1. SCADA/DCS Supervisório
- Monitoramento centralizado de todos os processos produtivos em tempo real
- Visualização de status de equipamentos, alarmes e eventos
- Controle remoto de setpoints e parâmetros operacionais (com autenticação multifator)
- Gestão de alarmes com priorização inteligente e notificações contextuais

### 3.2. Coleta e Integração de Dados IIoT
- Conectividade com múltiplos protocolos industriais (Modbus, OPC-UA, MQTT, DNP3, Profinet, EtherNet/IP)
- Ingestão de dados de sensores em alta frequência (até 1kHz para aplicações críticas)
- Normalização e contextualização de dados de fontes heterogêneas
- Edge computing para pré-processamento e redução de latência

### 3.3. Manutenção Preditiva com IA
- Modelos de machine learning para previsão de falhas em equipamentos rotativos
- Análise de vibração, temperatura e consumo energético para detecção de anomalias
- Recomendações automáticas de intervenções de manutenção
- Integração com sistemas CMMS (Computerized Maintenance Management System)

### 3.4. Controle de Qualidade Automatizado
- Inspeção visual automatizada com visão computacional e deep learning
- Rastreabilidade completa de lotes e componentes (track & trace)
- Controle estatístico de processo (CEP/SPC) em tempo real
- Detecção automática de desvios e acionamento de ações corretivas

### 3.5. Gestão de Energia e Sustentabilidade
- Monitoramento de consumo energético por linha, equipamento e produto
- Identificação de oportunidades de eficiência energética
- Integração com sistemas de gestão de utilities (ar comprimido, vapor, água)
- Relatórios de pegada de carbono e indicadores ESG

### 3.6. Digital Twin (Gêmeo Digital)
- Réplicas virtuais de linhas de produção e equipamentos críticos
- Simulação de cenários "what-if" para otimização de processos
- Testes de mudanças de configuração em ambiente virtual antes da implementação física
- Treinamento de operadores em ambiente seguro

### 3.7. Dashboards e Analytics em Tempo Real
- Painéis executivos com KPIs de produção, qualidade, eficiência e segurança
- Análises de OEE (Overall Equipment Effectiveness) e perdas de produção
- Visualizações customizáveis por perfil de usuário
- Alertas proativos baseados em regras de negócio

### 3.8. Integração ERP/MES
- Sincronização bidirecional com sistemas ERP (SAP, TOTVS) para ordens de produção e consumo de materiais
- Integração com MES (Manufacturing Execution System) para gestão de receitas e genealogia de produtos
- APIs RESTful e webhooks para integração com sistemas de terceiros
- Barramento de integração baseado em padrões ISA-95

---

---

## 4. INFRAESTRUTURA TECNOLÓGICA

A infraestrutura da SmartFactory segue o **Purdue Model** (ISA-95/IEC 62443), um padrão de referência para arquitetura de redes industriais que define níveis hierárquicos de 0 a 5, com zonas de segurança e conduits (canais de comunicação controlados) entre elas.

### 4.1. Arquitetura Purdue Model

**Nível 0 — Processo Físico:**
- Sensores industriais (temperatura, pressão, vibração, fluxo, nível)
- Atuadores (válvulas, motores, drives de frequência variável)
- Dispositivos de campo com protocolos analógicos (4-20mA, 0-10V) e digitais (HART, Foundation Fieldbus)

**Nível 1 — Controle Básico:**
- 120 PLCs (Siemens S7-1500, Allen-Bradley ControlLogix, Schneider Modicon)
- Controladores de segurança (Safety PLCs) para funções SIL 2/3
- Drives e inversores de frequência com comunicação industrial
- Protocolos: Modbus RTU/TCP, Profinet, EtherNet/IP

**Nível 2 — Supervisão e Controle:**
- 8 servidores SCADA/DCS (Wonderware System Platform, Ignition SCADA)
- 45 estações HMI (interfaces operador-máquina)
- Historiadores de dados (OSIsoft PI System, Wonderware Historian)
- Servidores OPC-UA para interoperabilidade
- Rede Ethernet industrial redundante (anel RSTP/MRP)

**Nível 3 — Operações de Manufatura:**
- Sistemas MES (Manufacturing Execution System) — Siemens Opcenter
- CMMS (Computerized Maintenance Management) — SAP PM
- LIMS (Laboratory Information Management System) para controle de qualidade
- Servidores de aplicação da SmartFactory Platform (edge analytics, digital twin)
- Banco de dados de produção (PostgreSQL TimescaleDB, InfluxDB para séries temporais)

**Nível 4 — Gestão de Negócios:**
- ERP corporativo (SAP S/4HANA)
- Sistemas de BI (Business Intelligence) — Power BI, Tableau
- CRM (Customer Relationship Management) para clientes SaaS
- Sistemas de gestão de documentos e qualidade (ISO 9001)

**Nível 5 — Rede Corporativa:**
- Infraestrutura IT convencional (Active Directory, Exchange, SharePoint)
- Acesso à Internet corporativa
- VPN para acesso remoto de colaboradores

### 4.2. Protocolos Industriais e Comunicação

A SmartFactory utiliza múltiplos protocolos industriais, muitos dos quais foram projetados décadas atrás sem considerações de segurança cibernética:

**Protocolos Legados (sem segurança nativa):**
- **Modbus TCP/RTU:** Protocolo amplamente utilizado, mas sem autenticação ou criptografia nativa
- **DNP3:** Comum em utilities, vulnerável a ataques de replay e man-in-the-middle
- **Profinet/Profibus:** Protocolos Siemens com segurança limitada em versões antigas

**Protocolos Modernos (com recursos de segurança):**
- **OPC-UA (Unified Architecture):** Padrão IEC 62541 com autenticação, criptografia e controle de acesso granular
- **MQTT com TLS:** Protocolo leve para IoT com suporte a criptografia e autenticação
- **HTTPS/REST APIs:** Para integração com sistemas de nível superior

**Desafio de Segurança:** A coexistência de protocolos legados e modernos cria uma superfície de ataque heterogênea. Protocolos sem segurança nativa devem ser protegidos através de segmentação de rede, firewalls industriais e monitoramento de anomalias.

### 4.3. Cloud Industrial e Edge Computing

A SmartFactory adota uma arquitetura híbrida cloud-edge:

**Edge Computing (On-Premises):**
- Servidores edge em cada planta para processamento local de dados críticos
- Latência ultra-baixa (<10ms) para controles em tempo real
- Autonomia operacional em caso de perda de conectividade com cloud
- Tecnologias: Docker containers, Kubernetes K3s, Azure IoT Edge

**Cloud Industrial (AWS/Azure):**
- Data lake para armazenamento de dados históricos de longo prazo (Amazon S3, Azure Data Lake)
- Plataforma de analytics e machine learning (AWS SageMaker, Azure ML)
- Ambientes multi-tenant para clientes SaaS da plataforma
- Backup e disaster recovery geograficamente distribuído
- Serviços gerenciados: bancos de dados, message brokers (AWS IoT Core, Azure IoT Hub)

**Conectividade:**
- Links dedicados MPLS entre plantas e cloud (redundância 4G/5G)
- VPN site-to-site com criptografia IPSec
- Firewall de borda com inspeção profunda de pacotes (DPI)

### 4.4. Redes OT Segregadas

A segmentação de rede é um controle fundamental para limitar a propagação de ataques:

**Zonas de Segurança:**
- **Zona de Processo (Níveis 0-1):** Rede isolada com PLCs e dispositivos de campo, sem acesso direto à Internet
- **Zona de Controle (Nível 2):** SCADA/HMI com acesso controlado via firewalls industriais
- **Zona de Operações (Nível 3):** MES/CMMS com conectividade limitada a sistemas corporativos
- **DMZ Industrial:** Zona desmilitarizada para servidores de integração (OPC-UA, APIs) entre OT e IT
- **Rede Corporativa (Níveis 4-5):** Rede IT convencional com acesso à Internet

**Conduits (Canais de Comunicação):**
- Firewalls industriais (Fortinet FortiGate, Palo Alto Networks) entre zonas
- Regras de firewall baseadas em whitelist (apenas tráfego explicitamente permitido)
- Inspeção de protocolos industriais (DPI para Modbus, DNP3, OPC-UA)
- Diodos de dados (data diodes) unidirecionais para extração segura de dados de zonas críticas

### 4.5. Sistemas SCADA/DCS/PLC/HMI

**SCADA (Supervisory Control and Data Acquisition):**
- Wonderware System Platform e Ignition SCADA
- Monitoramento centralizado de múltiplas plantas
- Gestão de alarmes e eventos
- Relatórios de produção e KPIs

**DCS (Distributed Control Systems):**
- Sistemas de controle distribuído para processos contínuos
- Redundância de controladores e redes
- Controle regulatório avançado (PID, cascata, feedforward)

**PLC (Programmable Logic Controllers):**
- Siemens S7-1500, Allen-Bradley ControlLogix, Schneider Modicon
- Programação em linguagens IEC 61131-3 (Ladder, FBD, ST, SFC)
- Ciclos de scan determinísticos (tipicamente 10-100ms)
- Firmware com assinatura digital e boot seguro (em modelos recentes)

**HMI (Human-Machine Interface):**
- Painéis de operador em chão de fábrica (Siemens Comfort Panels, Allen-Bradley PanelView)
- Estações de trabalho com software SCADA
- Interfaces touch-screen industriais (IP65, resistentes a ambientes agressivos)

**Desafio de Atualização:** Muitos PLCs e HMIs possuem ciclos de vida de 15-20 anos e não podem ser facilmente substituídos ou atualizados. Patches de segurança são raros e, quando disponíveis, requerem paradas de produção para aplicação, criando um dilema entre segurança e disponibilidade.

---