# Imagem do portal ViaSerra: site estático servido pelo Nginx
FROM nginx:1.27-alpine

LABEL maintainer="Enzo Schmitt Lima" \
      matricula="26175314"

# Coloca o site na pasta padrão de onde o Nginx serve os arquivos
COPY html/ /usr/share/nginx/html/

# Porta em que o Nginx escuta dentro do container
EXPOSE 80
