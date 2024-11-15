# repositorioexamen1evaluacionadrianchillonmillara
Crea un repositorio para contestar todo o exame.
Este repositorio ten que conter tódo-los ficheiros necesarios para xustifica-la túas respostas.

Contesta as seguintes preguntas, xustificándoas, nun README.md

# 1. Explica métodos para 'abrir' unha consola/shell a un contenedor en execución.

Uno de ellos es usar el comando docker exec -it
```
docker exec

docker exec -it [name_contenedor]
```

# 2. No contenedor anterior (en execución), qué opciones tes que ter usado ó arrincalo para poder interactuar coas súas entradas e salidas
Una de las principales opciones que se puede emplear para interactuar con sus entradas y salidas es el comando:
```
docker run -it [username]
```

# 3. Cómo sería un ficheiro docker-compose para que dous contenedores se comuniquen entre si nunha rede só deles?


# 4. Qué tes que engadir ó ficheiro anterior para que un contenedor teña unha IP fixa?
Hay que modificar primero el archivo que en este caso es el .yml
```
networks:
  red:
      driver: bridge
      ipam:
        config:
        - subnet: "172.28.0.0/16"  
```
Y posteriormente le cambio su ip por una ip que sea fija

```
 networks:
      red:
        ipv4_address: 172.28.5.2
``` 
```
# 5. Qué comando de consola podo usar para sabe-las ips dos contenedores anteriores?
Para saber las ips empleamos el comando a continuacion:

```
docker inspect -f
```
# 6. Cál é a funcionalidade do apartado "ports" en docker compose?

Se usa principalmente para mapear puertos de un contenedor  hacia los puertos de un host


# 7. Para qué serve o rexistro CNAME? Pon un exemplo

La función que tiene el registro CNAME  es redireccionar un dominio hacia otro   distinto

# 8. Cómo podo facer para que a configuración dun contenedor DNS non se borre se creo outro contenedor?

Para no tener que perder la configuración del DNS es mejor emplear unos buenos volumenes que en mi opinión es la mejor opción a escoger 

# 9. Engade unha zoa tendaelectronica.int no teu docker DNS que teña:
- www á IP 172.16.0.1
- owncloud sexa un CNAME de www
- un rexistro de texto có contido "1234ASDF"
Comproba que todo funciona có comando "dig"
Mostra nos logs que o servicio funciona ben usando a saída da terminal ó levantar o compose ou có comando "docker logs [nomeContenedorOuID]"
(o apartado 9 realízase na máquina virtual)
```
$TTL 3600


@	IN SOA	ns.tendaelectronica.int. admin.tendaelectronica.int (

202411501   ; serial
3600      ; refresh 
1000       ; retry (1 hour)
129660     ; expire (1 week)
3600      ; minimum 
				)
@		IN NS	ns.tendaelectronica.int.
ns		IN A		172.16.0.1  #Ip proporcionada por el enunciado
owncloud IN CNAME www
@		IN TXT	"1234ASDF"

```
