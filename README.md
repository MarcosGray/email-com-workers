# email-com-workers
Este é um projeto de estudo com o Docker com objetivo de aprender como montar vários contêineres com programas específicos se comunicando para a execução do envio de emails.

Para executar esse projeto é necessário que o Docker já esteja instalado.

### Estrutura do projeto
- Um container frontend com um servidor nginx e uma pagina html com formulário
- Um container backend com python 3.6
- Um container com banco de dados Postgres 9.6
- Um container com o Redis e 3 workers executando o processo de envio de email

Execute os passos abaixo para executar este projeto:

Os passos 3 e 3.1 são opcionais, podem ser usado o 3 ou 3.1 de acordo com o seu desejo.

### Passo 1: Baixar o projeto
git clone https://github.com/MarcosGray/email-com-workers.git

### Passo 2: Executar o projeto com 3 workers levantados
docker-compose up -d --scale worker=3

### Passo 3: Ver o log de funcionamento de todos os serviços (opcional)
- O comando abaixo mostra todos os serviços que foram levantados.
docker-compose logs -f -t

### Passo 3.1: Ver o log de funcionamento apenas dos workers (opcional)
- O comando abaixo mostra apenas os workers e os logs gerados por eles, quando são chamados.
docker-compose logs -f -t workers

### Para ver os containers que foram levantados use:
docker-compose ps

### Parando a execução de todos os containers (Projeto inteiro)
docker-compose down

### Para ver as informações salvas no banco Postres
docker-compose exec db psql -U postgres -d email_sender -c 'select * from emails' 

### Como posso ver o projeto funcionando
Abra uma página no seu navegador usando http://localhost
Em seguida preencha os campos e envie o formulario clicando em enviar.

### Erro que pode surgir
Se por acaso ao enviar o formulario o navegar mostrar o erro 404 not found, esse problema pode estar relacionado a você já ter um outro servidor default ativo no seu sistema operacional.

Para solucionar esse problema, desabilite-o e rode novamente os comando para levantar o projeto usando o código no passo 2.


