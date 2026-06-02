# Projeto Fase 2 — Relatório de Auditoria de Segurança da Informação

## Visão Geral

A Fase 2 do projeto da disciplina tem como propósito aprofundar os conhecimentos adquiridos na Fase 1, onde foi desenvolvida uma política de segurança da informação. 

Agora, o foco será a aplicação prática de conceitos de auditoria e análise de vulnerabilidades. As equipes deverão realizar simulações controladas de exploração de vulnerabilidades e documentar os resultados em um relatório técnico profissional. 

Esta etapa complementa a abordagem teórica anterior com uma visão prática, permitindo aos alunos vivenciar o processo de identificação, exploração e mitigação de riscos em um ambiente seguro e controlado.

## Objetivos do Projeto

O objetivo geral desta fase é a elaboração de um relatório técnico de auditoria, baseado em simulações controladas de exploração de vulnerabilidades.

Os objetivos específicos incluem:
- Compreender na prática as vulnerabilidades de segurança da informação.
- Simular explorações de vulnerabilidades em um ambiente acadêmico e controlado.
- Produzir evidências técnicas consistentes da simulação realizada.
- Analisar os riscos, impactos e possíveis causas associadas à vulnerabilidade.
- Propor controles e medidas de mitigação efetivas.
- Elaborar um relatório técnico com linguagem e estrutura profissionais.

## Regras Éticas e Limites da Atividade

> **Aviso Importante:** A ética profissional é um pilar fundamental da segurança da informação. Todas as atividades realizadas neste projeto devem estar em estrita conformidade com as regras abaixo.

- **Ambiente Controlado:** Todas as simulações devem ocorrer **apenas** em ambientes autorizados, próprios, laboratoriais ou deliberadamente vulneráveis (como máquinas virtuais, laboratórios locais ou aplicações *vulnerable by design*).
- **Proibição de Ataques Reais:** É expressamente **proibido** realizar ataques, varreduras ou qualquer tipo de exploração contra sistemas reais, infraestruturas de terceiros ou serviços públicos sem autorização explícita e documentada.
- **Proteção de Dados:** É proibida a coleta, exposição ou uso indevido de dados reais de terceiros. Qualquer dado utilizado na simulação deve ser fictício ou gerado para fins de teste.
- **Finalidade Acadêmica:** As demonstrações e o relatório têm finalidade **exclusivamente acadêmica e educativa**.
- **Responsabilidade:** O uso irresponsável de ferramentas de segurança ou a violação destas regras éticas poderá acarretar em penalidades acadêmicas e, dependendo da gravidade, sanções legais.

## Explorações de Vulnerabilidades

Cada equipe deverá trabalhar com **uma** das vulnerabilidades listadas abaixo, conforme definição ou sorteio prévio pelo professor. As simulações devem focar na compreensão do mecanismo da vulnerabilidade e nas formas de defesa.

### 1. Phishing Simulado
- **Descrição Geral:** Criação de uma campanha simulada de e-mails fraudulentos para testar a conscientização dos usuários.
- **Cenário Simulado:** Envio de e-mails de phishing inofensivos para os próprios membros da equipe, simulando uma página de login corporativa falsa (hospedada localmente).
- **Objetivo da Demonstração:** Mostrar como a engenharia social pode ser usada para roubar credenciais e avaliar a taxa de clique/interação.
- **Possíveis Evidências:** Capturas de tela do e-mail recebido, logs de acesso à página falsa (com dados ofuscados) e estatísticas da campanha simulada.
- **Medidas de Mitigação Esperadas:** Treinamento de conscientização em segurança, implementação de MFA (Múltiplo Fator de Autenticação) e filtros de e-mail.

### 2. Exploração de Vulnerabilidade em Aplicação Web (ex: XSS ou CSRF)
- **Descrição Geral:** Exploração de falhas em aplicações web que permitem a injeção de scripts ou ações não autorizadas.
- **Cenário Simulado:** Utilização de uma aplicação web vulnerável por design (ex: DVWA, OWASP Juice Shop) hospedada localmente para demonstrar um ataque de Cross-Site Scripting (XSS).
- **Objetivo da Demonstração:** Evidenciar como a falta de validação de entrada pode comprometer a sessão do usuário.
- **Possíveis Evidências:** Prints da injeção do payload, alertas exibidos no navegador e trechos do código-fonte vulnerável.
- **Medidas de Mitigação Esperadas:** Sanitização de entradas, codificação de saídas e uso de cabeçalhos de segurança (ex: CSP).

### 3. Esteganografia Aplicada à Ocultação de Informação
- **Descrição Geral:** Técnica de ocultar uma mensagem ou arquivo dentro de outro arquivo (como uma imagem ou áudio) sem alterar sua aparência perceptível.
- **Cenário Simulado:** Ocultação de um arquivo de texto contendo uma "senha secreta" dentro de uma imagem JPEG utilizando ferramentas específicas, seguida da extração da informação.
- **Objetivo da Demonstração:** Demonstrar como dados podem ser exfiltrados ou comunicações ocultas podem ocorrer contornando inspeções visuais.
- **Possíveis Evidências:** A imagem original, a imagem alterada, os comandos utilizados na ferramenta e o arquivo extraído com sucesso.
- **Medidas de Mitigação Esperadas:** Monitoramento de tráfego anômalo, análise de integridade de arquivos e restrição de uso de ferramentas não homologadas.

### 4. SQL Injection (Injeção de SQL)
- **Descrição Geral:** Inserção de comandos SQL maliciosos em campos de entrada de uma aplicação para manipular o banco de dados.
- **Cenário Simulado:** Exploração de um formulário de login vulnerável em um ambiente de laboratório (ex: DVWA) para contornar a autenticação ou extrair dados da tabela de usuários.
- **Objetivo da Demonstração:** Ilustrar o risco de consultas dinâmicas não parametrizadas e o impacto do acesso indevido ao banco de dados.
- **Possíveis Evidências:** Capturas de tela do formulário com o payload SQL, resultados da consulta extraída e logs do banco de dados.
- **Medidas de Mitigação Esperadas:** Uso de *Prepared Statements* (consultas parametrizadas), ORMs e validação rigorosa de entrada.

### 5. Simulação de Ataque DDoS em Ambiente Controlado
- **Descrição Geral:** Tentativa de esgotar os recursos de um sistema ou rede, tornando-o indisponível para os usuários legítimos.
- **Cenário Simulado:** Uso de ferramentas de teste de estresse (ex: LOIC, hping3) em uma rede virtual isolada (VMs locais) contra um servidor web de teste configurado pela equipe.
- **Objetivo da Demonstração:** Observar o comportamento do servidor sob alta carga e a interrupção do serviço.
- **Possíveis Evidências:** Gráficos de consumo de CPU/Memória do servidor alvo, logs de tráfego de rede (Wireshark) mostrando a inundação de pacotes e a indisponibilidade da página web.
- **Medidas de Mitigação Esperadas:** Configuração de firewalls, limitação de taxa (rate limiting), uso de CDNs e serviços de proteção anti-DDoS.

### 6. Engenharia Social (Baiting ou Pretexting)
- **Descrição Geral:** Manipulação psicológica de pessoas para que executem ações ou divulguem informações confidenciais.
- **Cenário Simulado:** Criação de um cenário documentado onde um pen-drive "perdido" (Baiting) contendo um arquivo executável inofensivo é deixado em um ambiente controlado, ou a simulação de uma ligação telefônica (Pretexting) solicitando informações, com o consentimento prévio dos participantes para fins de teste.
- **Objetivo da Demonstração:** Avaliar a suscetibilidade dos usuários a táticas de manipulação física ou verbal.
- **Possíveis Evidências:** Relato documentado do cenário, roteiro utilizado, número de interações bem-sucedidas e logs de execução do arquivo inofensivo.
- **Medidas de Mitigação Esperadas:** Campanhas de conscientização contínuas, políticas de mesa limpa e procedimentos rígidos de verificação de identidade.

### 7. Sniffing ou Captura de Tráfego em Rede Local Controlada
- **Descrição Geral:** Interceptação e análise do tráfego de dados que passa por uma rede.
- **Cenário Simulado:** Captura de pacotes em uma rede virtual (ex: VirtualBox/VMware) utilizando o Wireshark durante a transmissão de credenciais em texto claro (HTTP, Telnet ou FTP).
- **Objetivo da Demonstração:** Mostrar a importância da criptografia na transmissão de dados e como informações sensíveis podem ser facilmente capturadas em redes não seguras.
- **Possíveis Evidências:** Capturas de tela do Wireshark destacando os pacotes interceptados e a extração das credenciais em texto claro.
- **Medidas de Mitigação Esperadas:** Uso de protocolos criptografados (HTTPS, SSH, SFTP), segmentação de rede e uso de VPNs.

### 8. Backdoor em Ambiente Laboratorial
- **Descrição Geral:** Instalação de um método oculto para contornar a autenticação normal e obter acesso remoto a um sistema.
- **Cenário Simulado:** Criação de um executável malicioso (payload) utilizando ferramentas como Metasploit e execução em uma máquina virtual Windows de teste, estabelecendo uma conexão reversa (reverse shell) com a máquina atacante.
- **Objetivo da Demonstração:** Ilustrar como um invasor pode manter acesso persistente a um sistema comprometido.
- **Possíveis Evidências:** Comandos utilizados para gerar o payload, captura de tela da sessão reversa estabelecida e execução de comandos remotos básicos (ex: `ipconfig`, `whoami`).
- **Medidas de Mitigação Esperadas:** Uso de soluções de EDR/Antivírus atualizadas, monitoramento de conexões de rede anômalas e controle de execução de aplicativos.

### 9. Ransomware Simulado (Sem Dano Real)
- **Descrição Geral:** Malware que criptografa os arquivos da vítima e exige um resgate para fornecer a chave de descriptografia.
- **Cenário Simulado:** Desenvolvimento ou utilização de um script simples (ex: em Python) que criptografa e descriptografa arquivos de texto em um diretório específico de uma máquina virtual isolada, simulando o comportamento de um ransomware.
- **Objetivo da Demonstração:** Compreender o impacto da perda de acesso aos dados e a mecânica básica de criptografia usada por ransomwares.
- **Possíveis Evidências:** Arquivos originais, arquivos criptografados, a mensagem de resgate simulada e a restauração dos arquivos após a execução do script de descriptografia.
- **Medidas de Mitigação Esperadas:** Política de backups regulares e offline, segmentação de rede, treinamento de usuários e soluções de proteção de endpoint.

### 10. Ataque de Força Bruta ou Quebra de Autenticação em Ambiente Controlado
- **Descrição Geral:** Tentativa sistemática de adivinhar senhas ou chaves criptográficas testando todas as combinações possíveis ou usando dicionários.
- **Cenário Simulado:** Utilização de ferramentas como Hydra ou Burp Suite para realizar um ataque de dicionário contra um formulário de login de uma aplicação web de teste (ex: DVWA) ou um serviço SSH configurado com senhas fracas em uma VM.
- **Objetivo da Demonstração:** Demonstrar a fragilidade de senhas curtas e previsíveis frente a ataques automatizados.
- **Possíveis Evidências:** Captura de tela da ferramenta em execução, o dicionário utilizado (parcialmente) e o sucesso na obtenção da credencial correta.
- **Medidas de Mitigação Esperadas:** Políticas de senhas fortes, bloqueio de conta após tentativas falhas, implementação de MFA e monitoramento de logs de autenticação.

## Produto Final Esperado

O resultado final do trabalho de cada equipe será um **Relatório Técnico de Auditoria de Segurança da Informação**.

- **Formato de Entrega:** Arquivo em formato **PDF**.
- **Limite de Páginas:** O documento deve ter, no máximo, **40 páginas**.
- **Idioma:** O relatório deve ser escrito em **português brasileiro**.
- **Conteúdo Exigido:** O relatório deve conter evidências claras e documentadas da simulação realizada, tais como capturas de tela (prints), logs, tabelas, diagramas, fluxos ou outros registros pertinentes. É fundamental garantir que **nenhum dado real sensível seja exposto** nas evidências.

## Estrutura Obrigatória do Relatório Final

O relatório deve seguir uma estrutura padronizada e profissional, aplicável a qualquer uma das vulnerabilidades escolhidas. A estrutura mínima exigida é:

1. **Capa:** Título do projeto, nome da instituição, nome da disciplina, nome do professor, nomes e RAs dos integrantes da equipe, local e data.
2. **Histórico de Versões:** Tabela com versão, data, descrição das alterações e autor.
3. **Sumário:** Índice com as seções do documento e numeração de páginas.
4. **Resumo Executivo:** Visão geral do relatório, destacando a vulnerabilidade testada, os principais achados e a conclusão (máximo de 1 página).
5. **Introdução:** Contextualização do trabalho e apresentação do tema.
6. **Objetivos:** Descrição dos objetivos gerais e específicos da auditoria.
7. **Escopo e Limites da Auditoria:** Definição clara do que foi testado, o que ficou de fora e as restrições éticas e técnicas aplicadas.
8. **Descrição do Ambiente de Simulação:** Detalhamento da infraestrutura utilizada (hardware, software, VMs, redes, ferramentas).
9. **Fundamentação Teórica da Vulnerabilidade Explorada:** Explicação conceitual da vulnerabilidade, como ela funciona e por que ocorre.
10. **Metodologia Utilizada:** Passo a passo da abordagem adotada para a simulação (ex: reconhecimento, exploração, pós-exploração).
11. **Descrição da Simulação Realizada:** Relato detalhado das ações executadas durante o teste.
12. **Evidências e Provas da Simulação:** Apresentação das capturas de tela, logs e outros artefatos que comprovam o sucesso (ou falha) da simulação.
13. **Análise Técnica dos Resultados:** Interpretação das evidências e explicação técnica do impacto observado.
14. **Avaliação de Riscos e Impactos:** Análise do impacto que essa vulnerabilidade teria caso fosse explorada em um ambiente corporativo real (impacto financeiro, reputacional, operacional).
15. **Medidas de Controle e Mitigação:** Recomendações técnicas e processuais para corrigir a vulnerabilidade e prevenir incidentes futuros.
16. **Relação com Boas Práticas, Frameworks ou Normas:** Associação das medidas propostas com frameworks de segurança (ex: ISO 27001, NIST CSF, CIS Controls, OWASP, MITRE ATT&CK, LGPD), quando aplicável.
17. **Considerações Finais:** Conclusão da equipe sobre o aprendizado e a importância da segurança proativa.
18. **Referências:** Fontes bibliográficas, artigos, manuais e sites consultados, formatados adequadamente.
19. **Apêndices ou Anexos (Opcional):** Scripts desenvolvidos, logs extensos ou materiais complementares.

## Critérios de Aceitação

Para que o relatório seja aceito e avaliado, ele deve atender aos seguintes critérios fundamentais, independentemente da vulnerabilidade escolhida:

- **Contextualização:** Apresenta corretamente o contexto do projeto e os objetivos da auditoria.
- **Ambiente:** Descreve de forma clara e detalhada o ambiente controlado onde a simulação ocorreu.
- **Fundamentação:** Explica tecnicamente a vulnerabilidade estudada de maneira correta e compreensível.
- **Simulação Controlada:** Demonstra inequivocamente que a simulação foi realizada em um ambiente seguro e controlado.
- **Evidências:** Apresenta provas ou evidências suficientes e claras da execução da simulação.
- **Análise:** Realiza uma análise coerente dos riscos e impactos associados à vulnerabilidade.
- **Mitigação:** Propõe medidas de mitigação adequadas, realistas e tecnicamente viáveis.
- **Referências:** Utiliza referências técnicas confiáveis e alinha-se a boas práticas de mercado.
- **Qualidade:** Mantém organização estrutural, clareza na redação e qualidade textual profissional.
- **Ética:** Respeita rigorosamente os limites éticos e legais estabelecidos nas regras do projeto.

## Rubrica de Avaliação

O projeto da Fase 2 terá o valor total de **3,0 pontos**. A avaliação será baseada na seguinte rubrica:

| Critério de Avaliação | Pontuação Máxima | Descrição |
| :--- | :---: | :--- |
| **1. Capacidade de simulação e apresentação de provas/evidências [EM SALA DE AULA]** | **1,0 ponto** | Avalia a execução técnica da simulação, a clareza, relevância e veracidade das evidências apresentadas (prints, logs, etc.), comprovando a exploração no ambiente controlado. |
| **2. Contextualização, fundamentação e descrição do ambiente** | **0,5 ponto** | Avalia a clareza na definição dos objetivos, a explicação teórica da vulnerabilidade e o detalhamento da infraestrutura e metodologia utilizadas. |
| **3. Análise de riscos, impactos e resultados** | **0,5 ponto** | Avalia a capacidade da equipe de interpretar os resultados técnicos e traduzi-los em impactos de negócio e riscos reais. |
| **4. Medidas de controle, mitigação e alinhamento com frameworks** | **0,5 ponto** | Avalia a pertinência e aplicabilidade das soluções propostas para corrigir a vulnerabilidade, bem como a correlação correta com normas e frameworks de segurança (ex: OWASP, ISO 27001). |
| **5. Qualidade da redação, formatação e conformidade ética** | **0,5 ponto** | Avalia a organização do documento, clareza textual, uso correto do idioma, formatação conforme as regras, citações adequadas e o respeito incondicional às regras éticas e legais. |
| **Total** | **3,0 pontos** | |

**Escala de Desempenho por Critério:**
- **Insuficiente (10% da pontuação):** O critério não foi atendido ou apresenta falhas graves.
- **Regular (50% da pontuação):** O critério foi atendido parcialmente, necessitando de melhorias significativas.
- **Bom (80% da pontuação):** O critério foi atendido de forma satisfatória, com pequenos desvios.
- **Excelente (100% da pontuação):** O critério foi plenamente atendido, demonstrando alta qualidade e domínio do tema.

## Especificações de Formatação

O documento deve seguir as seguintes diretrizes de formatação:

- **Modalidade:** Trabalho em grupo.
- **Formato de Arquivo:** Entrega exclusivamente em formato PDF.
- **Extensão:** Máximo de 40 páginas (incluindo capa e anexos).
- **Tipografia:** Fonte Arial ou Times New Roman, tamanho 12 para o corpo do texto.
- **Espaçamento:** Espaçamento entre linhas simples ou 1,15.
- **Margens:** Margens padrão de 2 cm (superior, inferior, esquerda e direita).
- **Citações e Referências:** Devem seguir as normas da ABNT, preferencialmente a NBR 6023 (Referências) e NBR 10520 (Citações).
- **Idioma:** Português brasileiro.

## Orientações Finais aos Alunos

- **O Relatório é o Produto Principal:** Lembrem-se de que o foco da avaliação será o relatório final entregue. Mesmo que a simulação técnica tenha sido excelente, ela precisa estar muito bem documentada para receber a pontuação adequada.
- **Clareza nas Evidências:** A simulação deve ser documentada passo a passo de forma clara. As evidências devem comprovar inequivocamente a execução da atividade, mas **nunca** devem expor dados sensíveis, reais ou de terceiros.
- **Nível Profissional:** A profundidade técnica, a linguagem e a apresentação do documento devem ser compatíveis com um relatório acadêmico-profissional. Evitem coloquialismos e foquem na objetividade técnica.
- **Responsabilidade e Ética:** Reforçamos que qualquer técnica ofensiva ou de exploração deve ser tratada com a máxima responsabilidade. A execução deve ocorrer estritamente em ambiente autorizado e com finalidade puramente educacional. A segurança da informação constrói-se com ética e profissionalismo.
