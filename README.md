# 🕵️‍♂️ Web Fuzzer & Enumerator

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Security](https://img.shields.io/badge/CyberSecurity-000000?style=for-the-badge&logo=security&logoColor=white)
![Terminal](https://img.shields.io/badge/CLI-4D4D4D?style=for-the-badge&logo=windows-terminal&logoColor=white)

## 📌 Sobre o Projeto

Este projeto é uma ferramenta de linha de comando (CLI) focada em **Segurança da Informação e Pentest**, desenvolvida puramente em Python. 

O script automatiza o processo de **Fuzzing e Enumeração Web**, buscando por subdomínios ocultos e diretórios/arquivos não mapeados em um domínio alvo. Ele ajuda a mapear a superfície de ataque de aplicações web de forma rápida e eficiente.

### 🚀 Principais Funcionalidades
* **Enumeração de Subdomínios:** Identifica subdomínios ativos (HTTP 200) utilizando uma wordlist customizada.
* **Fuzzing de Caminhos (Paths):** Descobre painéis de admin, APIs e endpoints ocultos.
* **Customização de User-Agent:** Permite contornar bloqueios simples de WAF (Web Application Firewall) alterando o User-Agent da requisição.
* **Salvamento de Emergência (Graceful Exit):** Tratamento de interrupções (`Ctrl + C`). Se o usuário parar a varredura na metade, os resultados parciais são salvos automaticamente.

---

## ⚠️ Aviso Legal (Disclaimer)
**Esta ferramenta foi criada estritamente para fins acadêmicos e educacionais.** O uso deste script para atacar alvos sem o consentimento prévio mútuo é ilegal. O desenvolvedor não assume qualquer responsabilidade e não é responsável por qualquer uso indevido ou dano causado por este programa.

---

## 🛠️ Como Utilizar

### 1. Pré-requisitos
Certifique-se de ter o Python 3 instalado e a biblioteca `requests`.

```bash
# Instale as dependências
pip install requests
```

### 2. Sintaxe de Uso
O script utiliza o módulo `argparse` para gerenciar os argumentos via terminal.

```bash
python3 fuzzer.py [-h] [-u USER_AGENT] <dominio> <subdomain_wordlist> <path_wordlist> <output_file>
```

### 3. Exemplo Prático
Rodando uma varredura no site `exemplo.com.br`, passando as wordlists e definindo o arquivo de saída como `resultados.txt`:

```bash
python3 fuzzer.py site.com.br subdominios.txt diretorios.txt resultados.txt
```

Para usar um **User-Agent** específico (exemplo: fingir ser o navegador Mozilla):
```bash
python3 fuzzer.py -u "Mozilla/5.0" site.com.br subdominios.txt diretorios.txt resultados.txt
```

---

## 📂 Estrutura do Código
O script foi construído focando em modularidade e tratamento de erros:
* Uso de `requests` para chamadas HTTP e validação de status code.
* `argparse` para construção de uma interface de linha de comando robusta.
* Tratamento de exceções `ConnectionError` e `InvalidURL` para evitar que a ferramenta quebre durante varreduras longas.
