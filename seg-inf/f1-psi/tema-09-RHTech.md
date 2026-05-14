# Sistema 09 — RHTech

---

## 1. IDENTIFICAÇÃO DO SISTEMA

**Nome da Empresa:** RHSmart Tecnologia em Gestão de Pessoas Ltda.  
**Nome do Sistema:** RHSmart — Plataforma Integrada de Gestão de Recursos Humanos  
**Setor:** HRTech / Tecnologia de Gestão de Pessoas  
**Porte:** Empresa de médio porte (120 colaboradores diretos)  
**Ano de Fundação:** 2018 (fictício)  
**Sede:** São Paulo, SP, Brasil  
**Modelo de Negócio:** SaaS B2B (Software as a Service Business-to-Business)  
**Público-Alvo:** Empresas de médio e grande porte (100 a 10.000+ colaboradores)

---

---

## 2. CONTEXTO DE NEGÓCIO DETALHADO

### 2.1. Missão e Visão

**Missão:** Transformar a gestão de recursos humanos por meio de tecnologia inovadora, automatizando processos trabalhistas e proporcionando experiências digitais excepcionais para colaboradores, gestores e profissionais de RH, com segurança, conformidade legal e eficiência operacional.

**Visão:** Ser a plataforma líder em gestão de pessoas no Brasil até 2028, reconhecida pela excelência em segurança da informação, conformidade com LGPD e integração nativa com sistemas governamentais (eSocial, FGTS Digital, SEFAZ).

### 2.2. Modelo de Negócio

A RHSmart opera sob o modelo **SaaS B2B multi-tenant**, oferecendo uma plataforma completa de gestão de recursos humanos e folha de pagamento para empresas de médio e grande porte. O sistema é comercializado por meio de assinaturas mensais escalonadas de acordo com o número de colaboradores gerenciados, módulos contratados e nível de suporte técnico.

**Principais Diferenciais Competitivos:**
- Integração nativa e automatizada com eSocial, FGTS Digital, DIRF, RAIS e INSS
- Conformidade total com CLT (Consolidação das Leis do Trabalho) e legislação trabalhista brasileira
- Módulo avançado de proteção de dados sensíveis em conformidade com LGPD Art. 11
- Arquitetura multi-tenant com isolamento rigoroso de dados entre clientes
- APIs abertas para integração com ERPs, sistemas de benefícios e bancos

**Modelo de Receita:**
- Assinatura mensal por colaborador gerenciado (R$ 8 a R$ 25/colaborador/mês)
- Módulos premium: recrutamento e seleção, LMS (Learning Management System), avaliação de desempenho
- Serviços profissionais: implantação, migração de dados, treinamento e consultoria em conformidade LGPD

### 2.3. Usuários do Sistema

O RHSmart atende múltiplos perfis de usuários com necessidades e níveis de acesso distintos:

**Usuários Internos (Empresas Clientes):**
- **Profissionais de RH:** Gestão completa de colaboradores, folha de pagamento, benefícios, recrutamento, treinamento e relatórios trabalhistas
- **Gestores e Líderes:** Aprovação de férias, afastamentos, avaliação de desempenho, visualização de equipes e indicadores de pessoas
- **Colaboradores:** Acesso a holerite digital, solicitação de férias, atualização de dados cadastrais, ponto eletrônico, certificados de treinamento
- **Contadores e Auditores Externos:** Acesso restrito a relatórios fiscais, folha de pagamento, obrigações acessórias (DIRF, RAIS, eSocial)

**Usuários Administrativos (RHSmart):**
- **Administradores de Sistema:** Gestão de tenants, configuração de integrações, monitoramento de infraestrutura
- **Suporte Técnico:** Atendimento a clientes, resolução de incidentes, análise de logs
- **Equipe de Segurança e Compliance:** Auditoria de acessos, gestão de incidentes de segurança, conformidade LGPD

### 2.4. Escala de Operação

**Dados Operacionais (Maio de 2026):**
- **Empresas Clientes Ativas:** 1.850 organizações
- **Colaboradores Gerenciados:** Aproximadamente 420.000 trabalhadores
- **Transações Mensais de Folha:** 420.000 holerites processados/mês
- **Registros de Ponto Eletrônico:** ~8,4 milhões de marcações/mês
- **Eventos eSocial Transmitidos:** ~2,1 milhões de eventos/mês
- **Volume de Dados Armazenados:** 18 TB (dados estruturados) + 45 TB (documentos digitalizados)
- **Disponibilidade do Sistema:** SLA de 99,5% (uptime mensal)

### 2.5. Integrações Críticas

O RHSmart mantém integrações técnicas complexas com múltiplos sistemas externos, essenciais para o cumprimento de obrigações legais e operação do negócio:

**Integrações Governamentais:**
- **eSocial (Governo Federal):** Transmissão automatizada de eventos trabalhistas (admissões, demissões, afastamentos, folha de pagamento, acidentes de trabalho) via webservices SOAP/REST
- **FGTS Digital (Caixa Econômica Federal):** Envio de informações de recolhimento do FGTS e conectividade social
- **SEFAZ (Secretarias da Fazenda Estaduais):** Geração e transmissão de DIRF (Declaração do Imposto de Renda Retido na Fonte) e RAIS (Relação Anual de Informações Sociais)
- **INSS (Instituto Nacional do Seguro Social):** Cálculo e envio de contribuições previdenciárias, GFIP (Guia de Recolhimento do FGTS e de Informações à Previdência Social)

**Integrações Financeiras:**
- **Bancos (Itaú, Bradesco, Santander, Banco do Brasil, Caixa):** Geração de arquivos CNAB 240/400 para pagamento de salários, benefícios e encargos via API bancária
- **Operadoras de Benefícios:** Integração com planos de saúde (Unimed, Bradesco Saúde, SulAmérica), vale-refeição/alimentação (Alelo, Sodexo, VR Benefícios), vale-transporte

**Integrações Corporativas:**
- **ERPs (SAP, TOTVS, Oracle):** Sincronização de centros de custo, estrutura organizacional e contabilização de folha
- **Sistemas de Ponto Eletrônico:** Importação de marcações de relógios biométricos (REP-P) e aplicativos móveis
- **Plataformas de Recrutamento:** Integração com LinkedIn Recruiter, Gupy, Kenoby para importação de candidatos

---

---

## 3. PRINCIPAIS FUNCIONALIDADES

O RHSmart oferece um conjunto abrangente de funcionalidades organizadas em módulos integrados:

### 3.1. Gestão de Folha de Pagamento
- Cálculo automatizado de folha de pagamento com base em CLT, convenções coletivas e acordos sindicais
- Gestão de rubricas (proventos, descontos, bases de cálculo)
- Cálculo de encargos sociais (INSS, FGTS, IRRF, contribuições sindicais)
- Geração de obrigações acessórias (eSocial, DIRF, RAIS, CAGED)
- Simulação de folha e análise de impacto de reajustes salariais
- Geração de arquivos CNAB para pagamento bancário

### 3.2. Ponto Eletrônico Digital
- Registro de ponto via aplicativo móvel com geolocalização
- Integração com relógios de ponto biométricos (REP-P)
- Tratamento de jornadas flexíveis, banco de horas e escalas de trabalho
- Cálculo automatizado de horas extras, adicional noturno e DSR (Descanso Semanal Remunerado)
- Espelho de ponto digital para aprovação de gestores
- Conformidade com Portaria MTP 671/2021 (ponto eletrônico)

### 3.3. Recrutamento e Seleção (ATS - Applicant Tracking System)
- Publicação de vagas em múltiplos canais (site da empresa, LinkedIn, Indeed)
- Gestão de pipeline de candidatos com etapas customizáveis
- Triagem automatizada de currículos com IA
- Agendamento de entrevistas e avaliações técnicas
- Banco de talentos para futuras oportunidades
- Relatórios de eficiência do processo seletivo (time-to-hire, custo por contratação)

### 3.4. Onboarding e Offboarding Digital
- Fluxos automatizados de integração de novos colaboradores
- Assinatura digital de documentos admissionais (contrato de trabalho, termo de confidencialidade)
- Checklist de atividades para RH, TI e gestores
- Treinamentos obrigatórios de compliance e segurança da informação
- Processo estruturado de desligamento com entrevista de saída
- Gestão de devolução de equipamentos e revogação de acessos

### 3.5. Gestão de Benefícios
- Cadastro e administração de benefícios (plano de saúde, odontológico, vale-refeição, vale-transporte, seguro de vida)
- Integração com operadoras para inclusão/exclusão de beneficiários
- Gestão de elegibilidade e coparticipação
- Portal do colaborador para consulta e alteração de benefícios
- Cálculo de descontos em folha de pagamento

### 3.6. Avaliação de Desempenho
- Ciclos de avaliação configuráveis (anual, semestral, trimestral)
- Múltiplas metodologias: 90°, 180°, 360°, avaliação por objetivos (OKRs)
- Feedback contínuo e one-on-ones estruturados
- Planos de desenvolvimento individual (PDI)
- Relatórios de performance e identificação de talentos (nine-box)

### 3.7. Treinamento e Desenvolvimento (LMS Integrado)
- Catálogo de cursos online e presenciais
- Trilhas de aprendizagem por cargo e competência
- Gestão de certificações obrigatórias (NRs, compliance)
- Avaliação de eficácia de treinamentos
- Integração com plataformas externas (Udemy Business, Coursera)

### 3.8. Holerite Digital e Portal do Colaborador
- Acesso seguro a holerites via portal web e aplicativo móvel
- Histórico completo de pagamentos e descontos
- Informe de rendimentos para declaração de IRPF
- Atualização de dados cadastrais (endereço, telefone, dependentes)
- Solicitação de documentos (declaração de vínculo, carta de apresentação)

### 3.9. Gestão de Férias e Afastamentos
- Solicitação de férias pelo colaborador com aprovação do gestor
- Cálculo automatizado de férias individuais e coletivas
- Gestão de afastamentos (licença médica, maternidade, paternidade, acidente de trabalho)
- Integração com eSocial para envio de eventos S-2230 (afastamentos) e S-1200 (remuneração)
- Controle de períodos aquisitivos e concessivos

### 3.10. Relatórios Trabalhistas e Compliance
- Relatórios gerenciais de headcount, turnover, absenteísmo
- Análise de custos de pessoal por centro de custo e departamento
- Relatórios de diversidade e inclusão (gênero, raça, PcD)
- Auditoria de conformidade trabalhista (CLT, convenções coletivas)
- Dashboard executivo com indicadores de RH (KPIs)
- Exportação de dados para análise em BI externo (Power BI, Tableau)

---

---

## 4. INFRAESTRUTURA TECNOLÓGICA

### 4.1. Stack Tecnológico

**Backend:**
- **Linguagem:** Java 17 (Spring Boot 3.x) para APIs REST
- **Banco de Dados Relacional:** PostgreSQL 15 (multi-tenant com schema separation)
- **Banco de Dados NoSQL:** MongoDB 6.0 (armazenamento de documentos digitalizados, logs)
- **Cache:** Redis 7.0 (sessões de usuário, cache de consultas frequentes)
- **Fila de Mensagens:** RabbitMQ 3.12 (processamento assíncrono de folha, integração com eSocial)

**Frontend:**
- **Web Application:** React 18 com TypeScript, Material-UI
- **Mobile:** React Native (iOS e Android) para aplicativo de ponto eletrônico e portal do colaborador

**Infraestrutura Cloud:**
- **Provedor:** AWS (Amazon Web Services) - Região São Paulo (sa-east-1)
- **Compute:** ECS (Elastic Container Service) com Fargate para containers Docker
- **Storage:** S3 (documentos digitalizados, backups), EBS (volumes de banco de dados)
- **Rede:** VPC isolada, subnets privadas para bancos de dados, Application Load Balancer (ALB)
- **CDN:** CloudFront para distribuição de assets estáticos

**Segurança e Monitoramento:**
- **WAF:** AWS WAF (Web Application Firewall) com regras OWASP Core Rule Set
- **IDS/IPS:** AWS GuardDuty para detecção de ameaças
- **SIEM:** Splunk Enterprise para correlação de logs e análise de segurança
- **Monitoramento:** Prometheus + Grafana para métricas de aplicação, CloudWatch para infraestrutura
- **Gestão de Secrets:** AWS Secrets Manager para credenciais de banco de dados e APIs

### 4.2. Arquitetura Multi-Tenant SaaS

O RHSmart implementa arquitetura **multi-tenant com isolamento de dados por schema** (PostgreSQL):
- Cada empresa cliente possui um schema dedicado no banco de dados
- Isolamento lógico garante que queries de um tenant não acessem dados de outro
- Metadados de tenants (configurações, customizações) armazenados em schema compartilhado
- Vantagens: melhor isolamento de dados, facilita backup/restore por cliente, permite customizações por tenant
- Desafios: complexidade de gestão de schemas, necessidade de controles rigorosos de roteamento de queries

### 4.3. APIs de Integração com Governo

**eSocial:**
- Protocolo: SOAP/XML (webservices do eSocial)
- Autenticação: Certificado digital A1 ou A3 (ICP-Brasil) por empresa cliente
- Eventos implementados: S-1000 (informações do empregador), S-2200 (admissão), S-2299 (desligamento), S-2230 (afastamento), S-1200 (remuneração), S-1210 (pagamentos diversos), S-2240 (condições ambientais do trabalho - CAT)
- Gestão de certificados: armazenamento seguro em AWS Secrets Manager, renovação automatizada com alertas

**FGTS Digital:**
- Protocolo: REST API (Conectividade Social ICP)
- Autenticação: Certificado digital A1 (ICP-Brasil)
- Funcionalidades: envio de informações de recolhimento, consulta de situação cadastral

**SEFAZ (DIRF/RAIS):**
- Geração de arquivos em formato PGD (Programa Gerador de Declarações)
- Transmissão via Receitanet (DIRF) e portal Gov.br (RAIS)

### 4.4. Biometria para Ponto Eletrônico

**Captura e Armazenamento:**
- Captura de impressão digital via relógios de ponto REP-P (Registrador Eletrônico de Ponto Portátil) homologados pelo MTP
- Algoritmo de extração de minúcias (pontos característicos da impressão digital)
- **Armazenamento:** Template biométrico (hash irreversível), não a imagem da impressão digital
- Criptografia AES-256 para templates biométricos em repouso
- Transmissão via TLS 1.3 entre dispositivos e servidor

**Conformidade Legal:**
- Portaria MTP 671/2021: requisitos técnicos para ponto eletrônico
- LGPD Art. 11: dado biométrico é sensível, base legal = obrigação legal (CLT Art. 74)

### 4.5. Criptografia de Dados Sensíveis

**Dados em Repouso:**
- Criptografia de disco (EBS encryption) com chaves gerenciadas por AWS KMS
- Criptografia em nível de aplicação para campos sensíveis (salário, dados bancários, dados de saúde) usando AES-256-GCM
- Chaves de criptografia rotacionadas anualmente

**Dados em Trânsito:**
- TLS 1.3 obrigatório para todas as comunicações (APIs, frontend, integrações)
- Certificados SSL/TLS emitidos por CA confiável (Let's Encrypt ou DigiCert)
- HSTS (HTTP Strict Transport Security) habilitado

### 4.6. Módulo de Auditoria e Logs

**Logs de Auditoria:**
- Registro de todos os acessos a dados sensíveis (quem, quando, qual dado, ação realizada)
- Logs de alterações em dados críticos (salário, dados bancários, afastamentos)
- Logs de autenticação (login, logout, falhas de autenticação)
- Retenção de logs: 5 anos (conformidade com CLT e LGPD)

**Análise de Logs:**
- Correlação de eventos no Splunk para detecção de anomalias
- Alertas automatizados para acessos suspeitos (horários atípicos, volume anormal de consultas, acesso a dados de múltiplos colaboradores em curto período)

---
