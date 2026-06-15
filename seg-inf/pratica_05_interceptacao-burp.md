# Roteiro Prático: Demonstração de Vulnerabilidades Web com Burp Suite

Arquivo com o código do aplicativo inseguro de exemplo: [TaskManager](https://github.com/diegoquirino/facisa-gqs/blob/main/seg-inf/burp-demo-app.zip)

## Índice

1. [Visão Geral](#visão-geral)
2. [Objetivos de Aprendizado](#objetivos-de-aprendizado)
3. [Pré-requisitos](#pré-requisitos)
4. [Instalação da Aplicação](#instalação-da-aplicação)
5. [Configuração do Burp Suite](#configuração-do-burp-suite)
6. [Demonstrações Práticas](#demonstrações-práticas)
7. [Vulnerabilidades Identificadas](#vulnerabilidades-identificadas)
8. [Questões de Reflexão](#questões-de-reflexão)

---

## Visão Geral

Este roteiro apresenta uma demonstração prática de vulnerabilidades web comuns utilizando a ferramenta **Burp Suite Community Edition**. A aplicação **TaskManager Inseguro** foi desenvolvida intencionalmente com falhas de segurança para fins educacionais, permitindo que os alunos aprendam a identificar e explorar vulnerabilidades em um ambiente controlado.

A aplicação consiste em um sistema de gerenciamento de tarefas com autenticação de usuário, implementado com **vulnerabilidades intencionais** em:

- Autenticação e autorização
- Validação de entrada
- Proteção contra ataques CSRF
- Armazenamento seguro de credenciais
- Controle de acesso (IDOR)

---

## Objetivos de Aprendizado

Ao completar este roteiro prático, os alunos serão capazes de:

1. **Configurar o Burp Suite** como web proxy para interceptar tráfego HTTP/HTTPS
2. **Interceptar e analisar** requisições e respostas HTTP
3. **Identificar vulnerabilidades** em aplicações web através da análise de tráfego
4. **Modificar requisições** para explorar falhas de segurança
5. **Compreender o impacto** de vulnerabilidades comuns (OWASP Top 10)
6. **Aplicar conhecimentos** de segurança defensiva em desenvolvimento web

---

## Pré-requisitos

Antes de iniciar este roteiro, certifique-se de que possui:

- **Node.js 18+** instalado (verifique com `node --version`)
- **npm ou pnpm** para gerenciamento de pacotes
- **Burp Suite Community Edition** instalado (download em https://portswigger.net/burp/communitydownload)
- **Firefox ou Chrome** para navegação web
- **Conhecimento básico** de HTTP, HTML e JavaScript
- **Acesso a um terminal/console** para executar comandos

### Verificar Instalações

```bash
# Verificar Node.js
node --version

# Verificar npm
npm --version

# Ou verificar pnpm
pnpm --version
```

---

## Instalação da Aplicação

### Passo 1: Clonar ou Extrair a Aplicação

Se você recebeu a aplicação como um arquivo compactado:

```bash
# Extrair o arquivo
unzip burp-demo-app.zip
cd burp-demo-app
```

Ou se clonar de um repositório:

```bash
git clone <url-do-repositorio>
cd burp-demo-app
```

### Passo 2: Instalar Dependências

```bash
# Usando pnpm (recomendado)
pnpm install

# Ou usando npm
npm install
```

### Passo 3: Iniciar o Servidor de Desenvolvimento

```bash
# Usando pnpm
pnpm dev

# Ou usando npm
npm run dev
```

Você deverá ver uma saída similar a:

```
🚀 Servidor rodando em http://localhost:3000/

📝 Credenciais de teste:
   Usuário: admin / Senha: admin123
   Usuário: user / Senha: user123

⚠️  AVISO: Esta aplicação é INTENCIONALMENTE VULNERÁVEL para fins educacionais!
   Use apenas em ambientes de teste controlados.
```

### Passo 4: Verificar Acesso à Aplicação

Abra seu navegador e acesse:

```
http://localhost:3000
```

Você deverá ver a página de login da aplicação TaskManager.

---

## Configuração do Burp Suite

### Passo 1: Iniciar o Burp Suite

1. Abra o Burp Suite Community Edition
2. Clique em **"Start Burp"** para iniciar a aplicação
3. Aguarde o carregamento completo (pode levar alguns segundos)

### Passo 2: Configurar o Proxy no Navegador

#### Opção A: Configuração Manual no Firefox

1. Abra o Firefox
2. Clique no menu (☰) → **Preferências**
3. Vá para **Rede** → **Configurações**
4. Selecione **"Configuração manual de proxy"**
5. Configure:
   - **Proxy HTTP:** `127.0.0.1`
   - **Porta:** `8080`
   - **Usar este proxy também para HTTPS:** ✓ (marcar)
6. Clique em **OK**

#### Opção B: Usar a Extensão FoxyProxy (Recomendado)

1. Instale a extensão **FoxyProxy Standard** no Firefox:
   - Acesse https://addons.mozilla.org/firefox/addon/foxyproxy-standard/
   - Clique em **"Adicionar ao Firefox"**

2. Configure o proxy:
   - Clique no ícone do FoxyProxy (canto superior direito)
   - Clique em **"Opções"**
   - Clique em **"Adicionar"**
   - Preencha:
     - **Nome do Proxy:** Burp Suite
     - **Tipo:** HTTP
     - **IP:** 127.0.0.1
     - **Porta:** 8080
   - Clique em **"Salvar"**

3. Ative o proxy:
   - Clique no ícone do FoxyProxy
   - Selecione **"Burp Suite"** para ativar

### Passo 3: Aceitar o Certificado do Burp Suite

Quando você tentar acessar um site HTTPS através do Burp Suite, o navegador mostrará um aviso de certificado. Para aceitar:

1. Clique em **"Avançado"** ou **"Detalhes"**
2. Clique em **"Aceitar o Risco e Continuar"**

Alternativamente, você pode importar o certificado do Burp Suite no navegador:

1. No Burp Suite, vá para **Proxy** → **Options** → **Proxy Listeners**
2. Clique em **"Import / Export CA Certificate"**
3. Clique em **"Export"** → **"Certificate in DER format"**
4. Salve o arquivo como `burp.der`
5. No Firefox, vá para **Preferências** → **Privacidade e Segurança** → **Certificados**
6. Clique em **"Ver Certificados"** → **"Autoridades"**
7. Clique em **"Importar"** e selecione o arquivo `burp.der`

### Passo 4: Verificar a Interceptação

1. No Burp Suite, vá para a aba **Proxy** → **Intercept**
2. Certifique-se de que o botão **"Intercept is on"** está ativado
3. No navegador, acesse `http://localhost:3000`
4. Você deverá ver a requisição GET interceptada no Burp Suite

---

## Demonstrações Práticas

### Demonstração 1: Interceptar Credenciais em Texto Plano

**Objetivo:** Demonstrar como as credenciais são enviadas em texto plano via HTTP.

**Passos:**

1. **Ativar Interceptação:**
   - No Burp Suite, vá para **Proxy** → **Intercept**
   - Certifique-se de que **"Intercept is on"** está ativado

2. **Acessar a Aplicação:**
   - No navegador, acesse `http://localhost:3000`
   - A requisição GET será interceptada no Burp Suite

3. **Fazer Login:**
   - Clique em **"Forward"** para deixar a requisição passar
   - Na página de login, digite:
     - **Usuário:** `admin`
     - **Senha:** `admin123`
   - Clique em **"Entrar"**

4. **Analisar a Requisição POST:**
   - A requisição POST será interceptada no Burp Suite
   - Observe o corpo da requisição (request body):
     ```json
     {
       "username": "admin",
       "password": "admin123"
     }
     ```
   - **Vulnerabilidade:** As credenciais estão em texto plano, visíveis para qualquer um que intercepte o tráfego!

5. **Modificar a Requisição:**
   - No Burp Suite, você pode modificar os valores antes de enviar
   - Mude o username para `user` e a senha para `user123`
   - Clique em **"Forward"**
   - Observe que agora você fez login como um usuário diferente!

**Conceitos Abordados:**
- Importância de HTTPS
- Transmissão segura de credenciais
- Proteção contra ataques man-in-the-middle

---

### Demonstração 2: Analisar o Token de Autenticação

**Objetivo:** Demonstrar como o token é gerado e armazenado de forma insegura.

**Passos:**

1. **Fazer Login (com interceptação desativada):**
   - No Burp Suite, vá para **Proxy** → **Intercept**
   - Clique em **"Intercept is off"** para desativar a interceptação
   - Faça login com `admin` / `admin123`

2. **Examinar a Resposta:**
   - Vá para **Proxy** → **HTTP history**
   - Procure pela requisição POST para `/api/login`
   - Clique nela e vá para a aba **Response**
   - Observe a resposta:
     ```json
     {
       "message": "Login bem-sucedido",
       "token": "MQ==",
       "user": {
         "id": 1,
         "username": "admin"
       }
     }
     ```

3. **Decodificar o Token:**
   - No Burp Suite, vá para **Decoder**
   - Cole o token `MQ==` no campo de entrada
   - Selecione **"Base64"** como formato
   - Clique em **"Decode"**
   - O resultado é: `1:admin`
   - **Vulnerabilidade:** O token é apenas base64 do userId:username, sem assinatura ou encriptação!

4. **Criar um Token Falso:**
   - No **Decoder**, digite `2:user` no campo de entrada
   - Clique em **"Encode"** → **"Base64"**
   - O resultado é: `Mjp1c2Vy`
   - Copie este token

5. **Usar o Token Falso:**
   - Abra o console do navegador (F12)
   - Execute:
     ```javascript
     localStorage.setItem('authToken', 'Mjp1c2Vy');
     localStorage.setItem('username', 'user');
     location.reload();
     ```
   - Você agora está autenticado como o usuário `user` sem saber sua senha!

**Conceitos Abordados:**
- Importância de JWT com assinatura
- Armazenamento seguro de tokens
- Proteção contra falsificação de identidade

---

### Demonstração 3: IDOR (Insecure Direct Object Reference)

**Objetivo:** Demonstrar como acessar tarefas de outros usuários modificando o ID na URL.

**Passos:**

1. **Fazer Login como Admin:**
   - Faça login com `admin` / `admin123`
   - Você verá as tarefas do admin

2. **Ativar Interceptação:**
   - No Burp Suite, ative a interceptação novamente

3. **Carregar as Tarefas:**
   - Clique em **"Forward"** para deixar as requisições passarem
   - Observe as requisições GET para `/api/tasks` no HTTP history

4. **Explorar IDOR via Repeater:**
   - Clique com botão direito na requisição GET para `/api/tasks`
   - Selecione **"Send to Repeater"**
   - Na aba **Repeater**, você pode modificar a requisição

5. **Modificar o Token:**
   - Altere o header `Authorization` para usar o token do usuário `user`
   - Token do user: `Mjp1c2Vy` (2:user em base64)
   - Clique em **"Send"**
   - Observe que você agora vê as tarefas do usuário `user`!

6. **Deletar Tarefas de Outro Usuário:**
   - Vá para a aba **Repeater**
   - Mude o método de GET para DELETE
   - Mude a URL para `/api/tasks/1` (tarefa do admin)
   - Mantenha o token do user
   - Clique em **"Send"**
   - **Vulnerabilidade:** Você conseguiu deletar a tarefa do admin sem ser o proprietário!

**Conceitos Abordados:**
- Importância de validação de autorização
- Verificação de propriedade de recursos
- Proteção contra acesso não autorizado

---

### Demonstração 4: Injeção de Conteúdo (XSS)

**Objetivo:** Demonstrar como injetar conteúdo HTML/JavaScript na aplicação.

**Passos:**

1. **Fazer Login:**
   - Faça login com qualquer usuário

2. **Criar uma Tarefa com Conteúdo Malicioso:**
   - No campo **"Título"**, digite:
     ```html
     <img src=x onerror="alert('XSS Vulnerabilidade!')">
     ```
   - Clique em **"Adicionar Tarefa"**

3. **Interceptar a Requisição:**
   - No Burp Suite, você verá a requisição POST para `/api/tasks`
   - Observe que o conteúdo HTML é enviado sem sanitização

4. **Executar o Payload:**
   - Clique em **"Forward"** para deixar a requisição passar
   - A tarefa será criada com o conteúdo HTML
   - Quando a página recarregar, o JavaScript será executado
   - Um alerta será exibido: "XSS Vulnerabilidade!"

5. **Explorar via Repeater:**
   - Você pode usar o **Repeater** para enviar payloads mais complexos
   - Exemplos de payloads XSS:
     ```html
     <script>alert('XSS')</script>
     <img src=x onerror="fetch('/api/tasks')">
     <svg onload="alert('XSS')">
     ```

**Conceitos Abordados:**
- Importância de sanitização de entrada
- Proteção contra XSS (Cross-Site Scripting)
- Validação e escape de conteúdo

---

### Demonstração 5: Modificar Requisições com o Repeater

**Objetivo:** Demonstrar como usar o Repeater para testar diferentes cenários.

**Passos:**

1. **Enviar para o Repeater:**
   - Faça uma requisição qualquer (GET, POST, PUT, DELETE)
   - Clique com botão direito e selecione **"Send to Repeater"**

2. **Modificar e Reenviar:**
   - Na aba **Repeater**, você pode modificar qualquer parte da requisição:
     - **Método HTTP** (GET, POST, PUT, DELETE, etc.)
     - **Headers** (Authorization, Content-Type, etc.)
     - **Body** (parâmetros, JSON, etc.)
   - Clique em **"Send"** para enviar a requisição modificada

3. **Analisar a Resposta:**
   - Observe a resposta no painel direito
   - Compare com a resposta original para identificar diferenças

4. **Exemplos de Testes:**
   - Mudar o método de GET para DELETE
   - Remover o header Authorization
   - Modificar parâmetros no JSON
   - Adicionar parâmetros extras

---

## Vulnerabilidades Identificadas

A tabela abaixo resume as vulnerabilidades intencionais implementadas na aplicação:

| # | Vulnerabilidade | Localização | Impacto | Remediação |
|---|---|---|---|---|
| 1 | Credenciais em texto plano | Login POST | Interceptação de credenciais | Usar HTTPS, Hash de senhas |
| 2 | Token fraco (Base64) | Autenticação | Falsificação de identidade | Usar JWT com assinatura |
| 3 | Sem validação de entrada | Criação de tarefas | XSS, Injeção de código | Sanitizar e validar entrada |
| 4 | IDOR | GET/PUT/DELETE /api/tasks/:id | Acesso não autorizado | Validar propriedade do recurso |
| 5 | Sem proteção CSRF | POST /api/tasks | Requisições forjadas | Implementar CSRF tokens |
| 6 | Sem rate limiting | Login | Força bruta | Implementar rate limiting |
| 7 | Mensagens de erro reveladoras | Login | Enumeração de usuários | Mensagens genéricas |
| 8 | Armazenamento inseguro de token | localStorage | Roubo de token | Usar HttpOnly cookies |
| 9 | Sem paginação | GET /api/tasks | DoS | Implementar paginação |
| 10 | Sem validação de autorização | PUT/DELETE /api/tasks/:id | Modificação não autorizada | Verificar userId |

---

## Questões de Reflexão

Após completar as demonstrações práticas, reflita sobre as seguintes questões:

### Nível Conceitual

1. **Autenticação vs. Autorização:** Qual é a diferença entre autenticação e autorização? Como a aplicação falha em ambas?

2. **HTTPS vs. HTTP:** Por que é importante usar HTTPS em vez de HTTP? Quais são os riscos de usar HTTP para transmitir credenciais?

3. **Armazenamento de Senhas:** Por que as senhas nunca devem ser armazenadas em texto plano? Quais são as alternativas seguras?

4. **Tokens de Sessão:** Como um token de sessão seguro deveria ser implementado? Quais são os requisitos?

### Nível de Aplicação Prática

5. **Prevenção de XSS:** Como você prevenira ataques XSS em uma aplicação web? Quais são as técnicas de sanitização?

6. **Prevenção de IDOR:** Como você garantiria que um usuário só pode acessar seus próprios recursos?

7. **Proteção CSRF:** O que é um ataque CSRF? Como você implementaria proteção contra CSRF?

8. **Rate Limiting:** Por que o rate limiting é importante? Como você implementaria rate limiting para o endpoint de login?

### Nível de Design Seguro

9. **Princípio do Menor Privilégio:** Como você aplicaria este princípio no design da aplicação?

10. **Defense in Depth:** Como você implementaria múltiplas camadas de segurança para proteger a aplicação?

---

## Recursos Adicionais

### Documentação Oficial

- **Burp Suite:** https://portswigger.net/burp/documentation
- **OWASP Top 10:** https://owasp.org/www-project-top-ten/
- **OWASP Cheat Sheets:** https://cheatsheetseries.owasp.org/

### Ferramentas Recomendadas

- **Burp Suite Community Edition:** https://portswigger.net/burp/communitydownload
- **OWASP ZAP:** https://www.zaproxy.org/
- **Postman:** https://www.postman.com/

### Cursos e Tutoriais

- **PortSwigger Web Security Academy:** https://portswigger.net/web-security
- **HackTheBox:** https://www.hackthebox.com/
- **TryHackMe:** https://tryhackme.com/

---

## Avisos de Segurança

⚠️ **IMPORTANTE:** Esta aplicação foi desenvolvida intencionalmente com vulnerabilidades para fins educacionais. **NUNCA** use este código em produção ou em ambientes não controlados.

### Recomendações de Segurança para Produção

1. **Use HTTPS** em vez de HTTP
2. **Hash de senhas** com algoritmos seguros (bcrypt, Argon2)
3. **Implemente JWT** com assinatura e expiração
4. **Valide e sanitize** todas as entradas do usuário
5. **Implemente autorização** em todos os endpoints
6. **Use CSRF tokens** em formulários
7. **Implemente rate limiting** em endpoints sensíveis
8. **Use HttpOnly cookies** para armazenar tokens
9. **Implemente logging e monitoramento** de segurança
10. **Realize auditorias de segurança** regularmente

---

## Conclusão

Este roteiro prático forneceu uma visão abrangente de como identificar e explorar vulnerabilidades web comuns usando o Burp Suite. Os conceitos e técnicas apresentados são fundamentais para o desenvolvimento seguro de aplicações web.

Lembre-se: **segurança é um processo contínuo**, não um destino. Mantenha-se atualizado sobre as ameaças e vulnerabilidades mais recentes, e sempre aplique as melhores práticas de segurança no desenvolvimento de suas aplicações.

**Disciplina:** Segurança da Informação  
**Data:** 2026
