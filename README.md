el modulo mod_push -> src -> mod_push.erl debe estar en los modulos de contribucion /home/azureuser/docker-modules/.ejabberd-modules:/root/.ejabberd-modules
modifcas el archivo .erl 
bajas el compouse docker-compose down
comenta la linea  # - /home/azureuser/docker-modules/ebin/mod_push.beam:/opt/ejabberd-24.02/lib/ejabberd-24.2.0/ebin/mod_push.beam para liberar el modulo pre compilado 
subes el compouse docker-compose up
entras el contenedor docker exec -it ejabberd sh
compilas el modulo con ejabberdctl compile ~/.ejabberd-modules/sources/ejabberd-contrib/mod_push/src/mod_push.erl
buscas el compilado dentro del contenedor en la ruta /opt/ejabberd-24.02/lib/ejabberd-24.2.0/ebin/mod_push.beam
copias el archivo mod_push.beam a la maquina fuera del container 
docker cp ejabberd:/opt/ejabberd-24.02/lib/ejabberd-24.2.0/ebin/mod_push.beam /home/azureuser/docker-modules/ebin/
decomentas el map del compouse - /home/azureuser/docker-modules/ebin/mod_push.beam:/opt/ejabberd-24.02/lib/ejabberd-24.2.0/ebin/mod_push.beam
subes el compouse en modo servicio con  docker-compose up -d 
