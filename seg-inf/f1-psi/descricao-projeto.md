# PROJETO FASE 01 - POLÍTICA DE SEGURANÇA DA INFORMAÇÃO (PSI)

## 📋 VISÃO GERAL

O PROJETO DA FASE 1 consiste no desenvolvimento de uma **Política de Segurança da Informação (PSI)** completa para um sistema fictício sorteado para o grupo.

---

## 🎯 OBJETIVOS DO PROJETO

- Aplicar frameworks internacionais de segurança (ISO 27001, NIST CSF 2.0, CIS Controls v8)
- Mapear ameaças utilizando MITRE ATT&CK
- Garantir conformidade com LGPD e regulamentações "setoriais"
- Desenvolver análise de riscos estruturada
- Produzir documentação técnica profissional: **Política de Segurança da Informação (PSI)** (nível estratégico e tático)

---

## 📚 ESTRUTURA DO PROJETO

### PARTE 1: Descritivos dos 10 Sistemas de Software

Cada grupo será sorteado para **UM** dos seguintes sistemas fictícios (e deverá ler a descrição completa do mesmo, seguindo o link acoplado ao nome do sistema):

1. [**Fintech — PayFlowBR**](./tema-01-FinTech.md)
   - Pagamentos digitais e microcrédito
   - 2,5 milhões de usuários
   - Desafios: Banco Central, LGPD, PCI DSS, Open Finance

2. [**HealthTech — MediConnect**](./tema-02-HealthTech.md)
   - Prontuário eletrônico e telemedicina
   - 5 milhões de pacientes
   - Desafios: Dados sensíveis de saúde, CFM, ANS, LGPD

3. [**GovTech — CidadãoDigital**](./tema-03-GovTech.md)
   - Portal de serviços públicos municipais
   - 8 milhões de cidadãos
   - Desafios: LAI, Dados Abertos, LGPD setor público

4. [**EdTech — EduVerso**](./tema-04-EdTech.md)
   - Plataforma de ensino a distância
   - 3 milhões de alunos
   - Desafios: Dados de menores, MEC, proctoring, LGPD

5. [**E-commerce — MercadoBrasil**](./tema-05-Ecommerce.md)
   - Marketplace multi-vendedor
   - 20 milhões de clientes
   - Desafios: CDC, PCI DSS, fraudes, LGPD

6. [**IoT Industrial/OT — SmartFactory**](./tema-06-IoT.md)
   - Automação de manufatura
   - 80 plantas industriais
   - Desafios: IEC 62443, MITRE ATT&CK ICS, NRs

7. [**LegalTech — JurisCloud**](./tema-07-LegalTech.md)
   - Gestão de processos jurídicos
   - 50 mil advogados
   - Desafios: Sigilo profissional, OAB, dados sensíveis

8. [**AgriTech — AgroConnect**](./tema-08-AgriTech.md)
   - Monitoramento de lavouras e cadeia de suprimentos
   - 5 mil produtores rurais
   - Desafios: MAPA, CAR, IoT, rastreabilidade

9. [**HRTech — RHSmart**](./tema-09-RHTech.md)
   - Gestão de RH e folha de pagamento
   - 500 mil funcionários gerenciados
   - Desafios: CLT, eSocial, dados sensíveis (saúde, biometria)

10. [**Smart City/Mobilidade — MobiliCidade**](./tema-10-SmartCity.md)
    - Transporte público inteligente
    - 10 milhões de usuários
    - Desafios: Mobilidade urbana, geolocalização, benefícios sociais

---

### PARTE 2: Template de Relatório PSI

#### A) NÍVEL ESTRATÉGICO

1. **Declaração de Missão de Segurança**
   - Statement de compromisso da organização

2. **Objetivos Estratégicos de Segurança**
   - No mínimo 05 (cinco) objetivos SMART
   - **SMART**: **S (Specific): Definem exatamente o que precisa ser feito (ex: implementar, reduzir, etc.); **M (Measurable)**: Utilizam métricas claras (ex: 99,99% de uptime, 95% de adesão, etc.); **A (Achievable):** São metas ambiciosas, mas tecnicamente viáveis; **R (Relevant):** Focam diretamente no risco de negócio (ex: fraude, vazamento de dados, indisponibilidade, etc.); **T (Time-bound)**: Possuem prazos definidos (ex: final de trimestre, fim de 2026, etc.).

3. **Governança de Segurança da Informação**
   - Estrutura organizacional (CISO-Chief Information Security Officer, DPO-Data Protection Officer, CTO-Chief Technology Officer, CSI-Comitê de Segurança da Informação)
   - Definir papéis e responsabilidades para cada ente da estrutura organização (mínimo 3 - três - no caso de CSI)

4. **Conformidade Legal e Regulatória**
   - Mapeamento de legislações "setoriais" aplicáveis, mínimo 03 (três)
   - Bases legais LGPD, mínimo 03 (três) finalidades
   - Direitos dos titulares

5. **Alinhamento com ISO 27001**
   - Escopo do SGSI
   - Política de alto nível

#### B) NÍVEL TÁTICO

1. **Controles ISO 27001:2022 (Anexo A)**
   - No mínimo 03 (três) controles priorizados
   - Justificativas de implementação, relacionado ao "setor" em que está inserido o sistema fictício.

2. **Padrões NIST Cybersecurity Framework (CSF) 2.0**
   - No mínimo 03 (cinco) subcategorias
   - Cobertura das 6 funções (Govern, Identify, Protect, Detect, Respond, Recover)

3. **Benchmarks CIS Controls v8**
   - No mínimo 03 (cinco) controles
   - Salvaguardas específicas por Grupo de Implementação (IG1/IG2/IG3)

4. **Requisitos OWASP**
   - OWASP Top 10 (2021), no mínimo 03 (três)
   - OWASP API Security Top 10 (2023) — se aplicável (participa do mínimo)
   - OWASP Mobile Top 10 — se aplicável (participa do mínimo)

5. **Mapeamento de Ameaças MITRE ATT&CK**
   - No mínimo 03 (três) técnicas relevantes
   - Framework apropriado (Enterprise / ICS / Mobile)
   - Mitigações recomendadas

6. **Plano de Tratamento de Riscos**
   - No mínimo 03 (três) riscos identificados
   - Avaliação de probabilidade e impacto / Matriz de risco
   - Controles implementados
   - Risco residual - se aplicável

---

### PARTE 3: Rubrica de Avaliação (3,0 pontos)

**Critérios de avaliação transversais:**

| Critério | Peso | Descrição |
|----------|------|-----------|
| 1. Coerência e Completude da PSI | 1,0 | PSI completa, coerente e adaptada ao sistema |
| 2. Aplicação Correta dos Frameworks | 1,0 | Uso correto de ISO 27001, NIST CSF, CIS, OWASP, MITRE ATT&CK |
| 3. Qualidade da Análise de Riscos | 0,5 | Identificação, avaliação e tratamento de riscos |
| 4. Conformidade com LGPD e Regulamentações | 0,2 | Mapeamento legal e bases legais LGPD |
| 5. Clareza, Organização e Qualidade da Redação | 0,2 | Redação clara, terminologia técnica correta |
| 6. Uso de Referências e Fundamentação Técnica | 0,1 | Referências de qualidade, afirmações fundamentadas |
| **TOTAL** | **3,0** | |

**Escalas de desempenho para cada critério (percentual da pontuação que será aplicado):** Insuficiente (10%) / Regular (50%) / Bom (80%) / Excelente (100%)

---

## 📝 ESPECIFICAÇÕES DO RELATÓRIO

- **Formato:** Trabalho em grupo (até 6 alunos)
- **Extensão:** Até 20 páginas
- **Fonte:** Arial ou Times New Roman, tamanho 12
- **Espaçamento:** simples
- **Margens:** 2,0 cm
- **Referências e Citações:** NBR 10520 (citações) e a NBR 6023 (referências)
- **Idioma do Documento:** Português (BR)
- **Formato de entrega:** PDF

---

## 🔑 RESUMO DOS CRITÉRIOS DE COBERTURA MÍNIMA

### Nível Estratégico
- ✅ 1 Declaração de Missão
- ✅ 5+ (cinco) Objetivos Estratégicos SMART
- ✅ Estrutura organizacional (com 3+ papéis envolvidos no CSI)
- ✅ Mapeamento de 3+ legislações/normas
- ✅ Bases legais LGPD para 3+ finalidades
- ✅ Escopo do SGSI + Política de alto nível

### Nível Tático
- ✅ Mínimo 3+ (três) controles ISO 27001:2022
- ✅ Mínimo 3+ (três) subcategorias NIST CSF 2.0
- ✅ Mínimo 3+ (três) controles CIS Controls v8
- ✅ Mínimo 3+ (três) mapeamento OWASP Top 10
- ✅ Mínimo 3+ (três) técnicas MITRE ATT&CK
- ✅ Mínimo 3+ (três) riscos avaliados

---

## 🛠️ RECURSOS E FERRAMENTAS

### Documentação Oficial
- **ISO 27001:2022:** https://www.iso.org/standard/27001
- **NIST CSF 2.0:** https://www.nist.gov/cyberframework
- **CIS Controls v8:** https://www.cisecurity.org/controls
- **OWASP Top 10:** https://owasp.org/www-project-top-ten/
- **MITRE ATT&CK:** https://attack.mitre.org/
- **LGPD:** http://www.planalto.gov.br/ccivil_03/_ato2015-2018/2018/lei/l13709.htm

### Ferramentas Online
- **MITRE ATT&CK Navigator:** https://mitre-attack.github.io/attack-navigator/
- **NIST CSF Tools:** https://www.nist.gov/cyberframework/framework-tools
- **CIS Controls Navigator:** https://www.cisecurity.org/controls/cis-controls-navigator

---

## 🎓 DICAS PARA EXCELÊNCIA

1. **Seja específico:** Adapte todos os exemplos ao sistema escolhido
2. **Fundamente suas escolhas:** Justifique cada controle e técnica
3. **Use dados reais:** Pesquise estatísticas e casos do setor, quando precisar fornecer dados "setoriais"
4. **Demonstre integração:** Mostre como os frameworks se complementam
5. **Seja realista:** Considere limitações de recursos e maturidade
6. **Capriche na apresentação:** faça um documento limpo, padronizado e estruturado.
7. **Revise e refine:** Dedique tempo para revisão técnica e textual
8. **Cite suas fontes:** Referencie todas as afirmações técnicas
9. **Trabalhe em equipe:** Divida tarefas, mas garanta integração!
10. **Consulte o professor:** Tire dúvidas durante o desenvolvimento

---

**Boa sorte no desenvolvimento do trabalho!** 🚀

Este é um exercício desafiador que simula situações reais do mercado de trabalho. Aproveite a oportunidade para desenvolver competências essenciais em segurança da informação e proteção de dados.
