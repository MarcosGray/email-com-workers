# email-com-workers
Este é um projeto de estudo com o Docker com objetivo de aprender como montar vários contêineres com programas específicos se comunicando para a execução do envio de emails.

Para executar esse projeto é necessário que o Docker já esteja instalado.

## Estrutura do projeto
- Um container frontend com um servidor nginx e uma pagina html com formulário
- Um container backend com python 3.6
- Um container com banco de dados Postgres 9.6
- Um container com o Redis e 3 workers executando o processo de envio de email

Execute os passos abaixo para executar este projeto:

## Baixar o projeto
git clone https://github.com/MarcosGray/email-com-workers.git

## Executar o projeto com 3 workers levantados
docker-compose up -d --scale worker=3

## Ver o log de funcionamento de todos os serviços
docker-compose logs -f -t

## Ver o log de funcionamento apenas dos workers
docker-compose logs -f -t workers


