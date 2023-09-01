# Pipeline de Dados do Telegram

_Esse projeto foi desenvolvido para o curso Profissão: Analista de Dados da EBAC_


## Contexto

O objetivo do projeto é criar um sistema que captura mensagens em um grupo do Telegram e envia para um servidor na nuvem, possibilitando uma análise exploratória dos dados. Para isso foi utilizado um Chatbot, que interage com usuários e grupos através de conversas automatizadas. Ele armazena as mensagens enviadas no grupo.

## Arquitetura

![arquitetura]()

### Telegram
O Telegram fornece uma API que permite a conexão com os dados obtidos pelo Chatbot.

### AWS / Ingestão
Utilizamos o API Gateway para conectar com a API do Telegram. Após isso foi utilizado o Lambda com código Python para armazenar os dados em um bucket no S3 no formato json.

### AWS / ETL
Com os dados em json, foi utilizado o Lambda para transformar os dados para parquet e salvar em um outro bucket no S3. O Event Bridge serve para acionar o Lambda a cada 24 horas. 

### AWS / Apresentação
Depois da etapa ETL, utilizamos o Athena para poder criar a tabela que vai ser utilizada nas análises com consultas SQL.
## Análise Exploratória de Dados
