# Respostas · Avaliação Prática de Docker · ViaSerra Transportes (Turma C)

Nome: Enzo Schmitt Lima
Matrícula: 26175314
Usuário do GitHub: Enzo-Schmitt-Lima
Usuário do Docker Hub: enzoschmittlima

Responda com as suas palavras e com o que aconteceu na SUA máquina. Resposta curta e certa vale mais
do que texto longo copiado. Resposta que contradiz o seu próprio Dockerfile vale zero.

## Parte 1 · Dockerfile do portal

1. Qual imagem base você usou e qual o tamanho final da imagem do portal (saída de `docker images`)?

r: Usei a imagem base nginx:1.27-alpine. A imagem final enzoschmittlima/viaserra-portal:1.0-26175314 ficou com 73.6MB de uso em disco (21MB de conteúdo comprimido), segundo o docker images.

2. Em qual pasta do container o Nginx procura os arquivos do site? Mostre o comando que você usou para
   conferir que o `index.html` está lá dentro.
   
r: O Nginx serve os arquivos de /usr/share/nginx/html. Conferi com:
▎ docker exec teste-portal ls /usr/share/nginx/html
▎ A saída mostrou index.html e estilo.css.

## Parte 2 · Docker Hub

3. Nome completo da imagem publicada e link público do repositório no Docker Hub.

r: Imagem: enzoschmittlima/viaserra-portal:1.0-26175314
▎ Link: https://hub.docker.com/r/enzoschmittlima/viaserra-portal

4. Se você mudar o HTML, quais comandos precisa rodar para que a versão nova chegue ao Docker Hub?

r: Depois de alterar o HTML, reconstruo a imagem e envio de novo:
▎ docker build -t enzoschmittlima/viaserra-portal:1.0-26175314 ./portal
▎ docker push enzoschmittlima/viaserra-portal:1.0-26175314

## Parte 3 · Página de manutenção

5. Preencha uma linha por defeito encontrado. Defeito inexistente listado aqui desconta pontos.

┌─────┬───────────────────┬────────────────────┬────────────────────┬─────────────────────────┐
│  #  │     Instrução     │   O que estava     │  O que você viu    │      Como corrigiu      │
│     │                   │       errado       │     acontecer      │                         │
├─────┼───────────────────┼────────────────────┼────────────────────┼─────────────────────────┤
│     │                   │ A pasta pagina/    │ O build falhou com │                         │
│ 1   │ COPY pagina/ .    │ não existe; a      │  "/pagina": not    │ COPY site/ .            │
│     │                   │ página está em     │ found              │                         │
│     │                   │ site/              │                    │                         │
├─────┼───────────────────┼────────────────────┼────────────────────┼─────────────────────────┤
│     │                   │ O nginx roda em    │ O container ficou  │                         │
│ 2   │ CMD ["nginx"]     │ segundo plano e o  │ Exited (0) logo    │ CMD ["nginx", "-g",     │
│     │                   │ processo principal │ depois de subir    │ "daemon off;"]          │
│     │                   │  termina           │                    │                         │
├─────┼───────────────────┼────────────────────┼────────────────────┼─────────────────────────┤
│     │                   │ A página foi       │ O container ficou  │                         │
│ 3   │ WORKDIR           │ copiada fora da    │ de pé, mas         │ WORKDIR                 │
│     │ /usr/share/nginx  │ pasta servida pelo │ mostrava "Welcome  │ /usr/share/nginx/html   │
│     │                   │  Nginx             │ to nginx!"         │                         │
└─────┴───────────────────┴────────────────────┴────────────────────┴─────────────────────────┘


6. Qual a diferença entre `-p 7042:80` e `-p 80:7042` no `docker run`? Qual dos dois números é a porta do container?

r:No -p o formato é host:container. -p 7042:80 liga a porta 7042 do host à porta 80 do container. -p 80:7042 liga a porta 80 do host à porta 7042 do container, onde nada escuta. A porta do container é o número da direita.

## Parte 4 · Primeiro docker-compose

7. Escreva os dois comandos `docker run` que fariam o mesmo que o seu `docker-compose.yml`.

8. Qual comando derruba os dois containers de uma vez?

## Verificador

9. Código de conclusão impresso pelo verificador:

```
(cole aqui)
```
