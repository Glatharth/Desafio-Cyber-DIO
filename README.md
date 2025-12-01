# 🛡️ Desafio DIO: Pentest em Servidor FTP com Kali Linux

Este repositório documenta o projeto prático desenvolvido durante o **Bootcamp de Cibersegurança da DIO**. O objetivo deste desafio foi explorar vulnerabilidades no protocolo de transferência de arquivos (FTP) utilizando o **Kali Linux**, demonstrando o funcionamento de um ataque de força bruta e as respectivas medidas de proteção.

## 📋 Cenário e Objetivo

A atividade consistiu em realizar uma **Prova de Conceito (PoC)** em um ambiente controlado. O foco foi explorar a fragilidade de credenciais em serviços FTP, entender a sintaxe das ferramentas de auditoria e validar a segurança do sistema.

### 🛠️ Ferramentas Utilizadas
* **Sistema Operacional:** Kali Linux
* **Alvo:** Metasploitable 2 (Ambiente vulnerável em rede Host-Only)
* **Ferramenta de Ataque:** Medusa
* **Reconhecimento:** Nmap

---

## 🕵️‍♂️ Passo a Passo da Execução

### 1. Reconhecimento
Inicialmente, foi realizada uma varredura para identificar o endereço IP da máquina alvo e confirmar se a porta **21 (FTP)** estava aberta.

```bash
# Exemplo de verificação de porta
nmap -p 21 192.168.68.150
```

### 2. Preparação (Wordlist Personalizada)
Para este laboratório, optei por não utilizar listas massivas (como a rockyou). Em vez disso, criei manualmente um arquivo de texto contendo uma lista reduzida de senhas. Essa abordagem permitiu testar a eficácia dos comandos de forma ágil e focar no entendimento da lógica do ataque, garantindo que o teste fosse controlado e específico.

### 3. Execução do Brute Force
Utilizando a ferramenta Medusa, executei o comando apontando para o meu arquivo de senhas personalizado.

Comando utilizado:
```bash
medusa -h 192.168.56.101 -u msfadmin -P minha_wordlist.txt -M ftp -f
```

Explicação dos parâmetros:
 - -h 192.168.56.101: Endereço IP do alvo (Metasploitab)
 - -P minha_wordlist.txt: Caminho para o arquivo que criei com as senhas de teste.
 - -M ftp: Módulo específico para atacar o protocolo FTP.
 - -f: Stop on Found (Para a execução assim que a senha correta for encontrada).

### 4. Resultado
A ferramenta processou as entradas do meu arquivo e validou com sucesso a credencial, confirmando a vulnerabilidade.
