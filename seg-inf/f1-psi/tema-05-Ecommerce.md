# Sistema 05 — E-commerce / Marketplace

---

## 1. IDENTIFICAÇÃO DO SISTEMA

**Nome da Empresa:** MercadoBrasil S.A.  
**Nome do Sistema:** MercadoBrasil Marketplace  
**Setor:** E-commerce / Marketplace Multi-Vendedor  
**Porte:** Grande Porte (mais de 500 funcionários)  
**Ano de Fundação:** 2015 (fictício)  
**Sede:** São Paulo, SP, Brasil  
**Presença:** Nacional com operações em todas as regiões do Brasil

---

---

## 2. CONTEXTO DE NEGÓCIO DETALHADO

### 2.1. Missão e Visão

**Missão:** Conectar milhões de brasileiros a produtos e serviços de qualidade, democratizando o acesso ao comércio eletrônico e empoderando pequenos, médios e grandes vendedores através de uma plataforma tecnológica segura, eficiente e confiável.

**Visão:** Ser o marketplace mais confiável e inovador do Brasil até 2030, reconhecido pela excelência em experiência do usuário, segurança nas transações e compromisso com a proteção de dados pessoais e financeiros de todos os stakeholders.

### 2.2. Modelo de Negócio Marketplace Multi-Vendedor

O MercadoBrasil opera como um **marketplace multi-vendedor** (multi-seller), funcionando como intermediário tecnológico e comercial entre vendedores (sellers) e compradores finais. O modelo de negócio combina operações **B2C** (Business-to-Consumer) e **B2B** (Business-to-Business), permitindo que:

- **Vendedores Pessoa Física e Jurídica** cadastrem-se na plataforma, criem suas lojas virtuais, gerenciem catálogos de produtos, definam preços, controlem estoque e processem pedidos de forma autônoma.
- **Compradores Pessoa Física e Jurídica** naveguem por um catálogo unificado com milhões de produtos de diferentes sellers, comparem preços, avaliem reputação dos vendedores, realizem compras com múltiplos meios de pagamento e acompanhem a logística de entrega.

A plataforma monetiza através de:
- **Comissão sobre vendas** (percentual variável por categoria de produto, tipicamente entre 8% e 18%)
- **Taxas de intermediação financeira** (processamento de pagamentos)
- **Serviços de logística** (fulfillment opcional para sellers)
- **Publicidade e anúncios patrocinados** (destaque de produtos no marketplace)
- **Assinaturas premium** para sellers (planos com benefícios como menor comissão, analytics avançado, suporte prioritário)

### 2.3. Usuários e Stakeholders

O ecossistema do MercadoBrasil envolve múltiplos perfis de usuários com necessidades e permissões distintas:

#### 2.3.1. Compradores (Consumidores Finais)
- **Perfil:** Pessoas físicas e jurídicas que adquirem produtos na plataforma
- **Atividades:** Navegação, busca, comparação de preços, compra, pagamento, acompanhamento de pedidos, avaliação de produtos e sellers, solicitação de trocas/devoluções
- **Volume estimado:** 45 milhões de usuários cadastrados, 12 milhões de compradores ativos mensais

#### 2.3.2. Vendedores / Lojistas (Sellers)
- **Perfil:** Microempreendedores individuais (MEI), pequenas e médias empresas (PME), grandes varejistas e indústrias
- **Atividades:** Cadastro de produtos, gestão de estoque, precificação dinâmica, processamento de pedidos, gestão de logística, atendimento ao cliente, análise de desempenho de vendas
- **Volume estimado:** 280.000 sellers ativos, com 15.000 novos cadastros mensais

#### 2.3.3. Equipe Interna de Logística e Operações
- **Perfil:** Funcionários do MercadoBrasil responsáveis por operações de fulfillment, centros de distribuição e logística reversa
- **Atividades:** Recebimento de produtos, armazenagem, separação (picking), embalagem, expedição, gestão de devoluções
- **Volume estimado:** 3.500 colaboradores em 12 centros de distribuição

#### 2.3.4. Equipe Financeira e Antifraude
- **Perfil:** Analistas de risco, especialistas em prevenção de fraudes, equipe de conciliação financeira
- **Atividades:** Monitoramento de transações em tempo real, análise de padrões suspeitos, gestão de chargebacks, repasse financeiro para sellers, compliance PCI-DSS
- **Volume estimado:** 450 colaboradores especializados

#### 2.3.5. Administradores de Sistema e Suporte
- **Perfil:** Equipes de TI, segurança da informação, suporte técnico, atendimento ao cliente
- **Atividades:** Manutenção de infraestrutura, monitoramento de segurança, resposta a incidentes, suporte a sellers e compradores
- **Volume estimado:** 800 colaboradores

### 2.4. Escala de Operação

O MercadoBrasil opera em escala nacional com números expressivos que evidenciam a criticidade da segurança da informação:

- **Volume de Transações:** 8,5 milhões de pedidos processados mensalmente, com picos de até 450.000 pedidos/dia em datas promocionais (Black Friday, Cyber Monday, Dia do Consumidor)
- **SKUs (Stock Keeping Units):** Mais de 85 milhões de produtos únicos cadastrados no catálogo multi-seller
- **Sellers Ativos:** 280.000 vendedores, desde MEIs até grandes varejistas nacionais e internacionais
- **GMV (Gross Merchandise Value):** R$ 18 bilhões em volume bruto de mercadorias transacionadas anualmente
- **Tráfego Web e Mobile:** 320 milhões de visitas mensais, 75% via aplicativo mobile (iOS e Android)
- **Processamento de Pagamentos:** R$ 1,5 bilhão processados mensalmente através de múltiplos meios (PIX, cartões de crédito/débito, boleto bancário, BNPL - Buy Now Pay Later)

### 2.5. Ecossistema de Parceiros

A operação do marketplace depende de um ecossistema complexo de parceiros tecnológicos e operacionais:

#### 2.5.1. Transportadoras e Logística
- **Parceiros principais:** Correios, transportadoras regionais (Jadlog, Total Express, Azul Cargo), entrega expressa (Loggi, Lalamove para same-day delivery)
- **Integração:** APIs para cálculo de frete em tempo real, rastreamento de encomendas, gestão de SLA de entrega, logística reversa

#### 2.5.2. Adquirentes e Gateways de Pagamento
- **Parceiros:** Adquirentes (Stone, Cielo, Rede, PagSeguro), gateways de pagamento (Mercado Pago, PagBank), processadores PIX (integração direta com DICT do Banco Central)
- **Integração:** Tokenização de cartões, processamento 3DS (3D Secure), split de pagamento (repasse automático para sellers), conciliação financeira

#### 2.5.3. Antifraude e Análise de Risco
- **Parceiros:** ClearSale, Konduto, Sift, soluções proprietárias de machine learning
- **Integração:** Análise de risco em tempo real (score de fraude), validação de identidade, análise comportamental, device fingerprinting, verificação de dados cadastrais (CPF, CNPJ, endereço)

#### 2.5.4. Marketplaces de Nicho e Integrações B2B
- **Parceiros:** Integração com marketplaces verticais (moda, eletrônicos, livros), ERPs de sellers (TOTVS, SAP, Bling), plataformas de gestão de e-commerce (VTEX, Shopify)
- **Integração:** APIs RESTful para sincronização de catálogo, estoque, pedidos e preços

#### 2.5.5. Provedores de Infraestrutura Cloud
- **Parceiros:** AWS (Amazon Web Services) como provedor principal, Google Cloud Platform para serviços de IA/ML, CDN (Cloudflare, Akamai)
- **Integração:** Arquitetura multi-region para alta disponibilidade, disaster recovery, compliance com LGPD (data residency no Brasil)

---

---

## 3. PRINCIPAIS FUNCIONALIDADES

O MercadoBrasil oferece um conjunto abrangente de funcionalidades que suportam todo o ciclo de vida do comércio eletrônico multi-vendedor:

### 3.1. Catálogo Multi-Seller e Busca Inteligente
- Catálogo unificado com mais de 85 milhões de SKUs de 280.000 sellers
- Motor de busca com IA para relevância semântica, correção ortográfica, sinônimos e filtros avançados
- Recomendações personalizadas baseadas em histórico de navegação, compras anteriores e perfil comportamental
- Comparação de preços, condições de frete e reputação de sellers para o mesmo produto

### 3.2. Carrinho de Compras e Checkout Unificado
- Carrinho persistente multi-dispositivo (sincronização web/mobile)
- Checkout simplificado com opção de compra em um clique (one-click checkout) para usuários recorrentes
- Cálculo dinâmico de frete com múltiplas opções (econômico, expresso, same-day delivery)
- Aplicação automática de cupons de desconto, cashback e pontos de fidelidade

### 3.3. Gateway de Pagamento Multi-Meio
- **PIX:** Pagamento instantâneo com QR Code dinâmico, confirmação em tempo real
- **Cartões de Crédito/Débito:** Suporte a todas as bandeiras (Visa, Mastercard, Elo, Amex, Hipercard), parcelamento em até 12x, tokenização PCI-DSS
- **Boleto Bancário:** Geração de boleto registrado com vencimento configurável
- **BNPL (Buy Now Pay Later):** Parcerias com fintechs (Mercado Crédito, PicPay Parcelado) para crédito instantâneo
- **Carteiras Digitais:** Integração com Mercado Pago, PicPay, PayPal
- **Split de Pagamento:** Repasse automático para sellers após confirmação de entrega, com retenção de comissão e taxas

### 3.4. Gestão de Pedidos e Logística
- Painel unificado de acompanhamento de pedidos para compradores (status em tempo real, rastreamento de encomendas)
- Gestão de pedidos para sellers (notificações de novos pedidos, impressão de etiquetas, integração com transportadoras)
- Logística reversa automatizada (solicitação de troca/devolução, geração de código de postagem reversa, reembolso automático)
- SLA de entrega com penalidades para sellers em caso de atraso ou não cumprimento

### 3.5. Avaliações, Reputação e Confiança
- Sistema de avaliações de produtos (1 a 5 estrelas, comentários textuais, fotos/vídeos de clientes)
- Reputação de sellers (score baseado em volume de vendas, avaliações, taxa de cancelamento, tempo de resposta)
- Programa de "Seller Verificado" com selo de confiança para vendedores com histórico positivo
- Moderação de conteúdo (detecção de avaliações falsas, spam, conteúdo ofensivo)

### 3.6. Programa de Fidelidade e Cashback
- Programa de pontos (MercadoBrasil Points) acumulados a cada compra
- Cashback em compras selecionadas (percentual devolvido na carteira digital do usuário)
- Níveis de fidelidade (Bronze, Prata, Ouro, Platinum) com benefícios progressivos (frete grátis, descontos exclusivos, atendimento prioritário)

### 3.7. Painel do Seller (Seller Center)
- Dashboard com métricas de desempenho (vendas, conversão, ticket médio, avaliações)
- Gestão de catálogo (cadastro em massa via planilha, integração API, sincronização com ERP)
- Gestão de estoque em tempo real com alertas de ruptura
- Precificação dinâmica com sugestões baseadas em concorrência
- Relatórios financeiros (vendas, comissões, repasses, chargebacks)
- Central de atendimento ao cliente (chat integrado, tickets de suporte)

### 3.8. Antifraude em Tempo Real
- Análise de risco transacional com score de fraude (0-100) para cada pedido
- Validação de identidade (CPF/CNPJ, endereço, telefone, e-mail)
- Device fingerprinting (identificação de dispositivos suspeitos, detecção de emuladores/VPNs)
- Análise comportamental (padrões de navegação, velocidade de digitação, mouse movements)
- Regras de negócio customizáveis (bloqueio automático, revisão manual, aprovação condicional)
- Machine learning para detecção de fraudes emergentes (account takeover, fraude amigável, triangulação de cartões)

### 3.9. Aplicativo Mobile (iOS e Android)
- Aplicativo nativo com 75% do tráfego total da plataforma
- Notificações push para ofertas personalizadas, status de pedidos, mensagens de sellers
- Biometria para autenticação (Touch ID, Face ID, impressão digital Android)
- Modo offline para navegação de catálogo (sincronização posterior)
- Integração com carteiras digitais mobile (Apple Pay, Google Pay, Samsung Pay)

---

---

## 4. INFRAESTRUTURA TECNOLÓGICA

### 4.1. Stack Tecnológico Completo

O MercadoBrasil utiliza uma arquitetura moderna baseada em microserviços, cloud-native e altamente escalável:

#### 4.1.1. Frontend
- **Web:** React.js (SPA - Single Page Application), Next.js para SSR (Server-Side Rendering) e SEO
- **Mobile:** React Native para iOS e Android (código compartilhado), Swift/Kotlin para componentes nativos críticos
- **CDN:** Cloudflare e Akamai para distribuição de conteúdo estático (imagens, CSS, JS), cache de páginas, proteção DDoS

#### 4.1.2. Backend e Microserviços
- **Linguagens:** Java (Spring Boot) para serviços core, Node.js para APIs de alta concorrência, Python para serviços de IA/ML
- **Arquitetura:** Microserviços independentes para cada domínio de negócio (catálogo, pedidos, pagamentos, usuários, logística, avaliações, antifraude)
- **API Gateway:** Kong para roteamento, rate limiting, autenticação, logging centralizado
- **Mensageria:** Apache Kafka para eventos assíncronos (processamento de pedidos, notificações, sincronização de estoque), RabbitMQ para filas de tarefas

#### 4.1.3. Bancos de Dados
- **Relacional:** PostgreSQL (cluster multi-master) para dados transacionais críticos (pedidos, pagamentos, usuários)
- **NoSQL:** MongoDB para catálogo de produtos (schema flexível para diferentes categorias), Redis para cache de sessões e dados de alta frequência
- **Data Warehouse:** Amazon Redshift para analytics, BigQuery (GCP) para machine learning
- **Busca:** Elasticsearch para motor de busca de produtos, logs de aplicação e análise de segurança

#### 4.1.4. Infraestrutura Cloud
- **Provedor Principal:** AWS (Amazon Web Services)
- **Regiões:** Multi-region (São Paulo, Virgínia do Norte) para alta disponibilidade e disaster recovery
- **Compute:** EKS (Elastic Kubernetes Service) para orquestração de containers, EC2 para workloads específicos, Lambda para funções serverless
- **Storage:** S3 para armazenamento de imagens de produtos, documentos fiscais, backups; EBS para volumes de banco de dados
- **Rede:** VPC isolada, subnets privadas para bancos de dados, subnets públicas para load balancers, VPN para acesso administrativo

#### 4.1.5. Segurança e Monitoramento
- **WAF (Web Application Firewall):** AWS WAF + Cloudflare WAF para proteção contra OWASP Top 10
- **IDS/IPS:** AWS GuardDuty para detecção de ameaças, Suricata para análise de tráfego de rede
- **SIEM:** Splunk para correlação de logs, detecção de anomalias, resposta a incidentes
- **Monitoramento:** Prometheus + Grafana para métricas de infraestrutura e aplicação, Datadog para APM (Application Performance Monitoring)
- **Gestão de Secrets:** AWS Secrets Manager para credenciais, chaves de API, certificados

### 4.2. Integrações Críticas

#### 4.2.1. APIs de Pagamento
- **PIX:** Integração direta com DICT (Diretório de Identificadores de Contas Transacionais) do Banco Central via API Pix, geração de QR Code dinâmico, webhook para confirmação instantânea
- **Cartões:** Integração com adquirentes (Stone, Cielo) via API REST, suporte a 3DS 2.0 para autenticação forte, tokenização PCI-DSS
- **Boleto:** Integração com bancos emissores (Itaú, Bradesco, Banco do Brasil) via API de boleto registrado, webhook para confirmação de pagamento

#### 4.2.2. Integração com Transportadoras
- **APIs de Frete:** Integração com Correios (SIGEP Web), Jadlog, Total Express, Loggi para cálculo de frete em tempo real, geração de etiquetas, rastreamento de encomendas
- **Webhooks:** Notificações automáticas de eventos de logística (coleta realizada, em trânsito, saiu para entrega, entregue, tentativa de entrega, devolução)

#### 4.2.3. Ferramentas de IA e Machine Learning
- **Recomendação de Produtos:** Algoritmos colaborativos (collaborative filtering) e baseados em conteúdo (content-based), treinados em histórico de compras e navegação
- **Busca Semântica:** NLP (Natural Language Processing) com BERT para compreensão de intenção de busca, correção ortográfica, expansão de sinônimos
- **Antifraude:** Modelos de machine learning (Random Forest, XGBoost, redes neurais) treinados em milhões de transações históricas, detecção de anomalias em tempo real
- **Precificação Dinâmica:** Algoritmos de pricing para sellers baseados em concorrência, demanda, sazonalidade, elasticidade de preço

---
