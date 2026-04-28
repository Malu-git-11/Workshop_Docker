Passo a passo:



1: Abra o Docker desktop pelo pesquisar do Windows e espere aparecer "Your running containers show up here";



2 Criar repositório:



2.1: Acesse o GitHub

2.2: Clique em New repository

2.3: Nome: meu-projeto-Docker (ou qualquer nome que você quiser)

2.4: Marque Add README

2.5: Clique em Create repositor



3: Após criar o repositório github abra o terminal do computador (CMD (Prompt de comando));



4: Utilize esses comando no cmd / 1º - "git clone https://github.com/SEU-USUARIO/meu-projeto-docker.git"



4.1: "cd meu-projeto-Docker (ou o nome que você colocou)";



5 — Criar a estrutura do projeto: 



No terminal do computador (CMD (Prompt de comando)) utilize esses comandos: 

5.1: "mkdir app" (ou invés de "app" qualquer nome que você quiser)

5.2: "cd app" (ou o nome que você colocou)

5.3  "type nul > index.php"

5.4: "cd .."

5.5: "type nul > docker-compose.yml"

5.6: "type nul > dockerfile"

5.7: "dir" (Você verá como ficou o arquivo)





Resultado esperado: 



meu-projeto-docker/

│

├── docker-compose.yml

└── app

└── dockerfile

&nbsp;





6 - Criar PHP simples



no (CMD (Prompt de comando)) utilize o comando: 

"code ."



No VScode entre na pasta app (ou o nome que você colocou);

Clique no index.php



Na linha 1 cole esse código:



&nbsp;	<?php

&nbsp;	echo "<h1>Docker funcionando </h1>";



&nbsp;	$host = 'db';

&nbsp;	$user = 'root';

&nbsp;	$pass = '1234';

&nbsp;	$db = 'meubanco';



&nbsp;	$conn = new mysqli($host, $user, $pass, $db);



&nbsp;	if ($conn->connect\_error) {

&nbsp;   	die("Erro: " . $conn->connect\_error);

&nbsp;	}



&nbsp;	echo "Conectado ao banco!";

&nbsp;	?>



Após isso clique "Ctrl + s"

&nbsp;	

7 - Criar docker-compose



No VScode clique no arquivo docker-compose.yml;



Na linha 1 cole esse código:



version: '3.8'



services:



&nbsp; web:

&nbsp;   build: .

&nbsp;   container\_name: meu\_php

&nbsp;   ports:

&nbsp;     - "8080:80"

&nbsp;   volumes:

&nbsp;     - ./app:/var/www/html

&nbsp;   depends\_on:

&nbsp;     - db



&nbsp; db:

&nbsp;   image: mysql:5.7

&nbsp;   container\_name: meu\_mysql

&nbsp;   restart: always

&nbsp;   environment:

&nbsp;     MYSQL\_ROOT\_PASSWORD: 1234

&nbsp;     MYSQL\_DATABASE: meubanco

&nbsp;   ports:

&nbsp;     - "3306:3306"



&nbsp; phpmyadmin:

&nbsp;   image: phpmyadmin/phpmyadmin

&nbsp;   container\_name: meu\_phpmyadmin

&nbsp;   restart: always

&nbsp;   ports:

&nbsp;     - "8081:80"

&nbsp;   environment:

&nbsp;     PMA\_HOST: db



Após isso clique "Ctrl + s"





8 - Criar dockerfile



No VScode clique no arquivo docker-compose.yml;



Na linha 1 cole esse código:



FROM php:8.2-apache



RUN docker-php-ext-install mysqli \&\& docker-php-ext-enable mysqli





9 - Volte para o CMD e coloque o código:



"Docker-compose up -d"



Irá começar a criar o container



10 - acesse no google esse link: http://localhost:8080/





