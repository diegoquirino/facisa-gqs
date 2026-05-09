# Lição: Esteganografia com Steghide

## Índice

1. [Introdução aos Conceitos de Esteganografia](#1-introdução-aos-conceitos-de-esteganografia)
2. [Visão Geral da Ferramenta Steghide](#2-visão-geral-da-ferramenta-steghide)
3. [Instalação no GNU/Linux](#3-instalação-no-gnulinux)
4. [Prática Passo a Passo — Ocultando um Arquivo](#4-prática-passo-a-passo--ocultando-um-arquivo)
5. [Detalhamento de Parâmetros](#5-detalhamento-de-parâmetros)
6. [Verificação](#6-verificação)
7. [Extração](#7-extração)
8. [Dicas Úteis](#8-dicas-úteis)

---

## 1. Introdução aos Conceitos de Esteganografia

### 1.1 Origem e Definição

A palavra **esteganografia** vem do grego *steganos* (oculto, coberto) e *graphein* (escrever), significando literalmente "escrita oculta" ou "escrita secreta" [1]. Esta prática milenar consiste em ocultar a existência de uma mensagem secreta dentro de outro meio aparentemente inofensivo, de modo que observadores não suspeitem da presença de informação confidencial [1].

Ao longo da história, a esteganografia foi utilizada de diversas formas criativas. Desde mensagens escritas com tinta invisível (como suco de limão que se revela ao ser aquecido) até técnicas mais sofisticadas, o objetivo sempre foi o mesmo: esconder informações à vista de todos [1]. A esteganografia não é uma invenção moderna; ela tem sido praticada há séculos como forma de comunicação secreta e dissimulação [1].

### 1.2 Diferença entre Esteganografia e Criptografia

É fundamental compreender que **esteganografia não é criptografia**, embora ambas sejam técnicas de proteção de informações [1]. Vejamos as diferenças principais:

- **Criptografia**: Embaralha ou codifica os dados usando algoritmos e chaves, tornando a mensagem ilegível para quem não possui a chave de decifração. A existência da mensagem é óbvia, mas seu conteúdo é protegido. A criptografia é uma ciência que habilita a privacidade [1].

- **Esteganografia**: Oculta a própria existência da mensagem dentro de outro arquivo (imagem, áudio, documento). O observador não percebe que há dados secretos embutidos. A esteganografia é uma prática que habilita o sigilo e, potencialmente, o engano [1].

Em resumo: a criptografia protege o *conteúdo* da mensagem, enquanto a esteganografia oculta a *existência* da mensagem [1].

### 1.3 Uso em Segurança da Informação

No contexto moderno de segurança da informação, a esteganografia digital tem aplicações tanto legítimas quanto maliciosas:

**Aplicações legítimas:**
- Comunicação confidencial em ambientes hostis
- Marca d'água digital para proteção de direitos autorais
- Testes de penetração (pentest) para avaliar defesas organizacionais

**Aplicações maliciosas:**
- Atacantes utilizam esteganografia para ocultar scripts maliciosos dentro de documentos do Office (Word, Excel) [1]
- Entrega de malware, ransomware e trojans de forma furtiva [1]
- Exfiltração de dados sensíveis sem levantar suspeitas
- Comando e controle (C2) de botnets através de canais ocultos [1]

Profissionais de segurança da informação precisam compreender esteganografia para detectar ameaças avançadas e realizar análises forenses eficazes [1]. Analistas de segurança trabalham constantemente para identificar as táticas, técnicas e procedimentos (TTPs) utilizados por atacantes, incluindo assinaturas típicas de aplicações esteganográficas [1].

---

## 2. Visão Geral da Ferramenta Steghide

### 2.1 O que é o Steghide?

**Steghide** é um programa de esteganografia de código aberto capaz de ocultar dados em diversos tipos de arquivos de imagem e áudio [2]. Desenvolvido por Stefan Hetzl, o Steghide é uma das ferramentas mais populares e confiáveis para esteganografia em ambientes GNU/Linux, embora também esteja disponível para Windows e macOS [1], [2].

A principal característica do Steghide é sua capacidade de incorporar dados secretos sem alterar as frequências de cor (em imagens) ou de amostragem (em áudio), tornando a incorporação resistente a testes estatísticos de primeira ordem [2]. Isso significa que a imagem ou áudio modificado permanece visualmente/auditivamente idêntico ao original, dificultando a detecção.

### 2.2 Formatos Suportados

O Steghide suporta os seguintes formatos de arquivo como **arquivos de cobertura** (cover files) [2]:

- **JPEG** (.jpg, .jpeg) — formato de imagem comprimida
- **BMP** (.bmp) — formato de imagem bitmap
- **WAV** (.wav) — formato de áudio não comprimido
- **AU** (.au) — formato de áudio Sun/NeXT

O formato do arquivo é detectado automaticamente com base nas informações do cabeçalho, não pela extensão do arquivo [2]. Quanto aos **dados secretos** que você deseja ocultar, não há restrições de formato — pode ser qualquer tipo de arquivo (texto, PDF, executável, etc.) [2].

### 2.3 Como Funciona Internamente (Simplificado)

O Steghide utiliza uma abordagem baseada em teoria dos grafos para realizar a esteganografia [2]. Não é necessário conhecer teoria dos grafos para usar a ferramenta, mas entender o processo básico ajuda a apreciar sua sofisticação:

**Processo de incorporação (embedding):**

1. **Compressão e criptografia**: Os dados secretos são primeiro comprimidos (para ocupar menos espaço) e depois criptografados usando um algoritmo robusto [2].

2. **Geração de posições**: Com base em uma senha (passphrase) fornecida pelo usuário, um gerador de números pseudo-aleatórios cria uma sequência de posições de pixels (em imagens) ou amostras (em áudio) onde os dados serão incorporados [2].

3. **Otimização**: Posições que já contêm o valor correto por acaso são descartadas (não precisam ser modificadas) [2].

4. **Algoritmo de correspondência**: Um algoritmo de correspondência baseado em grafos encontra pares de posições cujos valores podem ser trocados para incorporar os dados secretos [2]. A maioria da incorporação é feita através de trocas, não sobrescrita.

5. **Finalização**: As posições restantes (que não fazem parte de pares) são modificadas por sobrescrita [2].

**Características de segurança:**

- **Criptografia padrão**: Rijndael-128 (AES) no modo CBC (Cipher Block Chaining) [2]
- **Verificação de integridade**: Checksum CRC32 automático para detectar corrupção [2]
- **Preservação estatística**: As estatísticas de primeira ordem (frequência de cores/amostras) não são alteradas, dificultando a detecção [2]

---

## 3. Instalação no GNU/Linux

A instalação do Steghide em distribuições GNU/Linux baseadas em Debian/Ubuntu é extremamente simples. O pacote está disponível nos repositórios oficiais.

### 3.1 Comando de Instalação

Abra um terminal e execute o seguinte comando com privilégios de superusuário:

```bash
sudo apt-get install steghide
```

O sistema solicitará sua senha de administrador e, em seguida, baixará e instalará o Steghide junto com suas dependências.

### 3.2 Verificação da Instalação

Após a instalação, você pode verificar se o Steghide foi instalado corretamente executando:

```bash
steghide --version
```

Você deverá ver informações sobre a versão instalada, confirmando que a ferramenta está pronta para uso.

---

## 4. Prática Passo a Passo — Ocultando um Arquivo

Agora vamos à parte prática! Nesta seção, você aprenderá a ocultar um arquivo de texto dentro de uma imagem JPEG usando o Steghide.

### 4.1 Preparação

Antes de começar, certifique-se de ter:

1. **Uma imagem JPEG** — para este exemplo, usaremos `Foto.jpg`
2. **Um arquivo de texto com dados secretos** — para este exemplo, usaremos `secreto.txt`

Coloque ambos os arquivos no mesmo diretório onde você executará os comandos, ou especifique o caminho completo.

### 4.2 Comando de Incorporação

Para ocultar o arquivo `secreto.txt` dentro da imagem `Foto.jpg`, execute o seguinte comando:

```bash
steghide embed -cf Foto.jpg -ef secreto.txt
```

**Explicação do comando:**
- `embed` — comando para incorporar dados
- `-cf Foto.jpg` — especifica o arquivo de cobertura (cover file)
- `-ef secreto.txt` — especifica o arquivo a ser incorporado (embed file)

### 4.3 Prompts e Saída Esperada

Após executar o comando, o Steghide solicitará que você defina uma senha (passphrase) para proteger os dados ocultos:

```
Enter passphrase: 
```

Digite uma senha forte e pressione Enter. **Atenção:** a senha não será exibida na tela enquanto você digita (por segurança).

Em seguida, o Steghide pedirá que você confirme a senha:

```
Re-Enter passphrase: 
```

Digite a mesma senha novamente e pressione Enter.

Se tudo correr bem, você verá a seguinte mensagem de sucesso:

```
embedding "secreto.txt" in "Foto.jpg"... done
```

**Importante:** Como não especificamos o parâmetro `-sf` (stego file), o Steghide modificará diretamente o arquivo `Foto.jpg`, incorporando os dados secretos nele [2]. Se você deseja preservar o arquivo original, use o parâmetro `-sf` para criar um novo arquivo (por exemplo, `-sf Foto_stego.jpg`).

### 4.4 O que Aconteceu?

Neste momento, o arquivo `Foto.jpg` contém os dados de `secreto.txt` ocultos dentro dele. Visualmente, a imagem parecerá idêntica à original. O nome do arquivo original (`secreto.txt`) também foi incorporado, facilitando a extração posterior [2].

---

## 5. Detalhamento de Parâmetros

O Steghide oferece diversos parâmetros para controlar o processo de incorporação e extração. Compreender esses parâmetros permite que você utilize a ferramenta de forma mais eficaz e segura.

### 5.1 Tabela de Parâmetros Principais

| Parâmetro | Nome Completo | Descrição | Exemplo de Uso |
|-----------|---------------|-----------|----------------|
| `-cf` | `--coverfile` | Especifica o arquivo de cobertura (imagem ou áudio) que será usado para incorporar dados. Formatos suportados: JPEG, BMP, WAV, AU. Se omitido ou definido como `-`, lê da entrada padrão [2]. | `-cf imagem.jpg` |
| `-ef` | `--embedfile` | Especifica o arquivo que será incorporado (dados secretos). O Steghide incorpora o nome original do arquivo no stego file. Se omitido ou definido como `-`, lê da entrada padrão [2]. | `-ef dados.txt` |
| `-sf` | `--stegofile` | Especifica o nome do arquivo stego que será criado (arquivo de saída). Se omitido no comando `embed`, as modificações são feitas diretamente no arquivo de cobertura. Se omitido no comando `extract`, os dados são salvos com o nome original incorporado [2]. | `-sf saida.jpg` |
| `-p` | `--passphrase` | Define a senha (passphrase) diretamente na linha de comando, sem prompts interativos. Se a senha contém espaços, deve ser colocada entre aspas. Útil para scripts, mas menos seguro (a senha fica visível no histórico do shell) [2]. | `-p "minha senha forte"` |
| `-e` | `--encryption` | Especifica o algoritmo de criptografia e/ou modo a ser usado. Pode ser seguido por um ou dois parâmetros (algoritmo e modo). Use `steghide encinfo` para ver algoritmos disponíveis. Padrão: `rijndael-128` (AES) no modo `cbc`. Use `-e none` para desabilitar criptografia [2]. | `-e rijndael-128 cbc` ou `-e none` |
| `-z` | `--compress` | Define o nível de compressão dos dados secretos antes da incorporação. Valores de 1 a 9, onde 1 = melhor velocidade e 9 = melhor compressão. A compressão reduz o tamanho dos dados, permitindo ocultar mais informações [2]. | `-z 9` |
| `-v` | `--verbose` | Ativa o modo verboso, exibindo informações detalhadas sobre o status do processo de incorporação ou extração. Útil para depuração e aprendizado [2]. | `-v` |
| `-f` | `--force` | Força a sobrescrita de arquivos existentes sem solicitar confirmação. Use com cuidado para evitar perda acidental de dados [2]. | `-f` |
| `-N` | `--dontembedname` | Não incorpora o nome do arquivo secreto no stego file. Se esta opção for usada, o extrator precisará especificar um nome de arquivo manualmente com `-xf` [2]. | `-N` |

### 5.2 Comando Especial: encinfo

O comando `encinfo` exibe uma lista de todos os algoritmos de criptografia e modos disponíveis no Steghide [2]:

```bash
steghide encinfo
```

Este comando não requer argumentos e é útil para conhecer as opções de criptografia suportadas pela sua instalação.

---

## 6. Verificação

Após ocultar dados em um arquivo, é importante verificar se o processo foi bem-sucedido e se a imagem parece normal.

### 6.1 Inspeção Visual

A primeira verificação é simples: abra a imagem modificada (`Foto.jpg`) em um visualizador de imagens ou navegador. A imagem deve parecer **exatamente igual** à original, sem distorções, artefatos ou alterações visíveis. Esta é uma das grandes vantagens do Steghide — a incorporação é imperceptível ao olho humano [2].

### 6.2 Comando info

O Steghide oferece o comando `info` para obter informações sobre um arquivo de cobertura ou stego file [2]. Este comando é extremamente útil para:

- Verificar a capacidade de um arquivo de cobertura
- Confirmar se um arquivo contém dados ocultos
- Obter informações sobre os dados incorporados (se você souber a senha)

**Sintaxe básica:**

```bash
steghide info Foto.jpg
```

**Saída esperada (exemplo):**

```
"Foto.jpg":
  format: jpeg
  capacity: 15.2 KB
Try to get information about embedded data ? (y/n) 
```

O Steghide exibe informações gerais sobre o arquivo (formato e capacidade) e pergunta se você deseja obter informações sobre dados incorporados. Se você responder `y` (yes), será solicitada a senha:

```
Enter passphrase: 
```

Digite a senha correta e pressione Enter. Se a senha estiver correta, você verá informações detalhadas sobre os dados ocultos:

```
embedded file "secreto.txt":
  size: 2.3 KB
  encrypted: rijndael-128, cbc
  compressed: yes
```

Estas informações confirmam que:
- O arquivo `secreto.txt` está incorporado
- Seu tamanho é 2.3 KB
- Está criptografado com Rijndael-128 (AES) no modo CBC
- Está comprimido

**Dica:** Se você fornecer uma senha incorreta, o Steghide não conseguirá extrair informações sobre os dados incorporados, mas isso não significa que não há dados ocultos — apenas que a senha está errada.

### 6.3 Comparação de Tamanho

Você pode comparar o tamanho do arquivo original com o arquivo modificado usando o comando `ls -lh`:

```bash
ls -lh Foto.jpg
```

O tamanho do arquivo pode aumentar ligeiramente devido aos dados incorporados, mas a diferença geralmente é pequena e não levanta suspeitas.

---

## 7. Extração

Agora que você ocultou dados com sucesso, vamos aprender a extraí-los. Este é o processo que o destinatário da mensagem secreta realizará.

### 7.1 Comando de Extração

Para extrair os dados ocultos do arquivo `Foto.jpg`, execute o seguinte comando:

```bash
steghide extract -sf Foto.jpg
```

**Explicação do comando:**
- `extract` — comando para extrair dados
- `-sf Foto.jpg` — especifica o stego file (arquivo que contém dados ocultos)

### 7.2 Prompts e Saída Esperada

Após executar o comando, o Steghide solicitará a senha:

```
Enter passphrase: 
```

Digite a senha que foi usada durante a incorporação e pressione Enter. **Atenção:** a senha deve ser exatamente a mesma; caso contrário, a extração falhará.

Se a senha estiver correta, você verá a seguinte mensagem de sucesso:

```
wrote extracted data to "secreto.txt".
```

O Steghide extraiu os dados ocultos e os salvou no arquivo `secreto.txt` no diretório atual. O nome do arquivo é o mesmo que foi incorporado originalmente [2].

### 7.3 Especificando um Nome de Arquivo Diferente

Se você deseja salvar os dados extraídos com um nome diferente, use o parâmetro `-xf` (extract file):

```bash
steghide extract -sf Foto.jpg -xf dados_extraidos.txt
```

Neste caso, os dados serão salvos em `dados_extraidos.txt` em vez de `secreto.txt`.

### 7.4 Verificação dos Dados Extraídos

Após a extração, você pode verificar o conteúdo do arquivo extraído:

```bash
cat secreto.txt
```

Ou abra o arquivo em um editor de texto. O conteúdo deve ser idêntico ao arquivo original que foi incorporado.

---

## 8. Dicas Úteis

Para usar o Steghide de forma eficaz e segura, considere as seguintes boas práticas e recomendações:

### 8.1 Senhas Fortes

- **Use senhas longas e complexas**: Combine letras maiúsculas, minúsculas, números e caracteres especiais. Senhas fracas podem ser quebradas por ataques de força bruta.
- **Evite senhas óbvias**: Não use palavras do dicionário, datas de nascimento ou informações pessoais.
- **Gerenciadores de senhas**: Considere usar um gerenciador de senhas para gerar e armazenar senhas fortes.
- **Compartilhamento seguro**: Nunca envie a senha pelo mesmo canal que o arquivo stego. Use um canal de comunicação separado e seguro.

### 8.2 Formatos Recomendados

- **JPEG para imagens**: É o formato mais comum e menos suspeito. Imagens JPEG são amplamente compartilhadas na internet, tornando-as ideais para esteganografia.
- **WAV para áudio**: Se você precisa ocultar dados em áudio, WAV é uma boa escolha devido à sua qualidade e capacidade.
- **Evite BMP quando possível**: Arquivos BMP são grandes e menos comuns, podendo levantar suspeitas.

### 8.3 Capacidade e Tamanho dos Arquivos

- **Verifique a capacidade**: Use `steghide info` para verificar a capacidade do arquivo de cobertura antes de tentar incorporar dados. Se os dados secretos forem maiores que a capacidade, a incorporação falhará.
- **Arquivos grandes**: Evite ocultar arquivos muito grandes em imagens pequenas. Isso pode causar falhas ou tornar a incorporação detectável.
- **Compressão**: Use o parâmetro `-z 9` para maximizar a compressão e reduzir o tamanho dos dados secretos [2].

### 8.4 Preservação do Arquivo Original

- **Use `-sf` para criar um novo arquivo**: Se você deseja manter o arquivo de cobertura original intacto, sempre especifique um nome de arquivo de saída com `-sf`:
  ```bash
  steghide embed -cf original.jpg -ef secreto.txt -sf stego.jpg
  ```
- **Backups**: Faça backup dos arquivos originais antes de modificá-los, especialmente se forem importantes.

### 8.5 Segurança Operacional

- **Não reutilize arquivos stego**: Após enviar um arquivo stego, não o reutilize para ocultar novos dados. Crie um novo arquivo de cobertura para cada operação.
- **Evite `-p` em ambientes compartilhados**: O parâmetro `-p` expõe a senha na linha de comando, que pode ser visível no histórico do shell ou em listas de processos. Use prompts interativos sempre que possível [2].
- **Limpeza de metadados**: Considere remover metadados EXIF de imagens antes de usá-las como arquivos de cobertura, para evitar rastreamento.

### 8.6 Detecção e Contramedidas

- **Análise forense**: Esteja ciente de que ferramentas de análise forense podem detectar esteganografia através de análise estatística avançada, mesmo que o Steghide seja resistente a testes de primeira ordem [2].
- **Uso ético**: Use esteganografia de forma ética e legal. Em contextos profissionais (pentesting, pesquisa), sempre obtenha autorização adequada.

### 8.7 Prática e Experimentação

- **Experimente diferentes parâmetros**: Teste diferentes níveis de compressão (`-z`), algoritmos de criptografia (`-e`) e formatos de arquivo para entender como cada um afeta o resultado.
- **Modo verboso**: Use `-v` durante o aprendizado para ver informações detalhadas sobre o processo [2]:
  ```bash
  steghide embed -cf Foto.jpg -ef secreto.txt -v
  ```
- **Comando encinfo**: Explore os algoritmos de criptografia disponíveis com `steghide encinfo` [2].

### 8.8 Documentação e Recursos

- **Manual do Steghide**: Consulte a página de manual completa com `man steghide` para informações detalhadas sobre todos os comandos e parâmetros.
- **Comunidade**: Participe de fóruns e comunidades de segurança da informação para aprender técnicas avançadas e manter-se atualizado sobre novas ferramentas e métodos.

---

## Conclusão

Parabéns! Você concluiu esta lição sobre esteganografia com Steghide. Agora você compreende os conceitos fundamentais de esteganografia, sabe como instalar e usar o Steghide para ocultar e extrair dados, e conhece as melhores práticas para usar esta ferramenta de forma eficaz e segura.

A esteganografia é uma habilidade valiosa para profissionais de segurança da informação, seja para realizar testes de penetração, análise forense ou simplesmente compreender as táticas usadas por atacantes. Continue praticando e explorando as capacidades do Steghide para aprofundar seu conhecimento.

Lembre-se sempre de usar essas técnicas de forma ética e responsável, respeitando as leis e regulamentos aplicáveis. Boa sorte em sua jornada no mundo da segurança da informação!

---

## Referências

[1] CompTIA. "The Ancient Practice of Steganography: What is it, How is it Used and Why Do Cybersecurity Pros Need to Understand it?" CompTIA Blog, 13 de novembro de 2024. Disponível em: https://www.comptia.org

[2] Ubuntu Manpages. "steghide - a steganography program." Ubuntu Focal Manual Pages. Disponível em: https://manpages.ubuntu.com/manpages/focal/man1/steghide.1.html
