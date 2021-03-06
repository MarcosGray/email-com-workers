# Email-com-workers
Este é um projeto de estudo com o Docker com objetivo de aprender como montar vários contêineres com programas específicos se comunicando para a execução do envio de emails de forma automatizada.

### Entendendo o projeto

A idéia desse projeto é mostrar como o docker funcionaria se aplicado em um servidor de e-mails, onde, várias pessoas fazem o preenchimento de um formulário e ao enviar estas informações, estas são armazenadas em um banco postgres e armazenada também em uma fila, nesse casso, foram levantados 3 workers que ficaram lendo a fila e enviando as informações gravadas.

A importancia aqui está em como fazer os containers se comunicarem, o uso do proxy reverso e como escalar algum processo.

Para executar esse projeto é necessário que o Docker já esteja instalado.

### Estrutura do projeto
- Um container frontend com um servidor nginx e uma pagina html com formulário
- Um container backend com python 3.6
- Um container com banco de dados Postgres 9.6
- Um container com o Redis e 3 workers executando o processo de fila e envio de email (representando apenas a idéia)

Execute os passos abaixo para executar este projeto:

Os passos 3 e 3.1 são opcionais, podem ser usado o 3 ou 3.1 de acordo com o seu desejo.

### Passo 1: Baixar o projeto
<code>git clone https://github.com/MarcosGray/email-com-workers.git</code>

### Passo 2: Executar o projeto com 3 workers levantados
<code> docker-compose up -d --scale worker=3 </code>

### Passo 3: Ver o log de funcionamento de todos os serviços (opcional)
- O comando abaixo mostra todos os serviços que foram levantados.

<code> docker-compose logs -f -t </code>

### Passo 3.1: Ver o log de funcionamento apenas dos workers (opcional)
- O comando abaixo mostra apenas os workers e os logs gerados por eles, quando são chamados.

<code> docker-compose logs -f -t workers </code>

### Para ver os containers que foram levantados use:
<code> docker-compose ps </code>

### Parando a execução de todos os containers (Projeto inteiro)
<code> docker-compose down </code>

### Para ver as informações salvas no banco Postgres
<code> docker-compose exec db psql -U postgres -d email_sender -c 'select * from emails' </code>

### Como posso ver o projeto funcionando
Abra uma página no seu navegador usando http://localhost

Em seguida preencha os campos e envie o formulario clicando em enviar, após o envio, deve carregar uma pagina com uma mensagem indicando que o envio foi realizado.

### Erro que pode surgir
Se por acaso ao enviar o formulario o navegar mostrar o erro 404 not found, esse problema pode está relacionado a você já ter um outro servidor default ativo no seu sistema operacional.

Para solucionar esse problema, desabilite-o e rode novamente os comando para levantar o projeto usando o código no passo 2.


