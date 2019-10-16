# Teste de filas

Esta aplicação é apenas um exemplo da utilização de filas para processamento no laravel.
Ao registrar-se como usuário um job é criado e será executado em uma fila com supervisor , a função é apenas um sleep mas pode ser substituida pela funcionalidade necessaria para seu sistema.

Dentro da pasta do projeto rode os seguintes comandos

```bash
composer install
npm install
npm run dev
cp .env.example .env
cd laradock
cp .env.example .env  #é isso mesmo não errei não tem que executar para o laradock.#
docker-compose up -d nginx phpmyadmin mysql php-worker
```

Serão criados os containers necessarios para o sistema rodar corretamente .
o banco de dados queue deve ser criado automaticamente ao rodar o docker-compose mas caso seja necessario cria-lo manualmente execute os seguintes comandos.

```bash
docker-compose exec mysql bash
mysql -u root -p < /docker-entrypoint-initdb.d/createdb.sql
exit
```

Para acessar o workspace da aplicação execute o seguinte comando:

```bash
docker-compose exec workspace bash
```

em seguida será possivel executar a migração.

```bash
php artisan migrate
```

para encerrar a execução do servidor laradock rode o seguinte comando:

```bash
docker-compose stop
```
