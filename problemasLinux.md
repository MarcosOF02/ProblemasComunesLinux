## <span style="color:#8181F7"> Soluciones a problemas comunes en linux</span>

#### <span style="color:#642EFE">Si hay problemas con un paquete de linux</span>
 
	Para reinstalar paquetes dañados utilizar: 
	- sudo apt install -f 

#### <span style="color:#642EFE">Problemas con resolución.</span>

	Vamos con sudo nano al archivo /etc/default/grub

	Buscamos la linea que pone: #GRUB_GFXMODE=640x480
	Y la ponemos asi: GRUB_GFXMODE=1920X1080

	Guardamos y ejecutamos el siguiente comando: sudo update-grub
	Reinicias el equipo y ya tienes la resolucion deseada.
	Si no funciona comprueba que tienes los drivers correspondientes actualizados en "Software y actualizaciones".

#### <span style="color:#642EFE">Cuando apagas el PC se reinicia.</span>

	Es un problema de algun pci (en algunos casos al menos), hay una opcion en la bios que desactivandola
	deja de reiniciarse. 
	
#### <span style="color:#642EFE">VM player no deja utilizar las maquinas virtuales.</span>

	Puede ser problema de la version del Kernel, prueba con una nueva o una anterior.
	
	Existe un programa que te lista las versiones disponibles y te las permite poner,
	tambien puedes habilitar el GRUB para poder seleccionar entre las versiones de kernel
	que se tienen puestas.
	
#### <span style="color:#642EFE">Problemas con la red.</span>

	Prueba a ejecurtar los siguientes comandos: ifdown y a continuación ifup y esperar unos segundos,
	si no se soluciona comprueba que la ip este en automatico y que el cable de red funcione correctamente.
	
	
#### <span style="color:#642EFE">Samba no deja acceder a carpeta compartida.</span>

	En el equipo que la compartes haz: sudo nano /etc/samba/smb.conf

	Y en el archivo busca la linea workgroup=WORKGROUP, y una linea debajo añade:
	server min protocol = NT1

#### <span style="color:#642EFE">Buscar equipos en la red:</span>

	- sudo nmap -sn 192.168.1.0/24  (La direccion de red, barra la mascara de red )

#### <span style="color:#642EFE">Utilizar resultado de un comando en la ejecución de otro.</span>

	para ello hay que utilizar '$(commando)' por ejemplo:
	- echo "Hola $(whoami)!"

	El comando anterior esta haciendo un "print" saludando al usuario que esta utilizandose

#### <span style="color:#642EFE">Ejecutar instrucciones bash tras x tiempo.</span>

	Esto puede servir para por ejemplo ejecutar scrips de python tras cierto tiempo por ejemplo entrenar una red despues de x minutos ya que hay una entrenandose y cuando acabe ya sera por la tarde, entonces asi puedes dejarlo para que se ejecute luego.
	
	Para hacer esto es de la siguiente manera:
	- at now + 180 minutes -f ej.sh (Se deben poner los comandos a ejecutar en un script .sh)
	
	En este caso se esta ejeutando "conda activate x" y a continuacion "python mainTrain.py" dentro de 180 minutos desde que se mando la instruccion "at"
	Para comprobar las tareas pendientes con el comando "at" se puede utilizar el comando "atq" 
	
	!!! Eliminar trabajo programado con "at"!!!
	Para ello es necesario utilizar atq, vemos el jobid del trabajo que queremos eliminar (el primer numero de la linea del trabajo en cuestion)
	Entonces se utiliza atrm "jobid"

	(Para apagar el pc el comando shutdown ya viene con una opcion para hacer lo mismo: shutdown -h tiempoEnMinutos, asi el pc se apagara despues de x tiempo)

#### <span style="color:#642EFE">Proceso tracker-miner-fs consume mucha CPU.</span>

	Este proceso es el encargado de indexar archivos y carpetas del sistema, pero si esta consumiendo demasiada CPU puede haber algun problema.
	La solucion seria resetearlo de la siguiente manera:
	- tracker reset --hard
	- tracker daemon --start

#### <span style="color:#642EFE">Ejecutar programa al arrancar el pc.</span>

	En el buscador del sistema busca: Aplicaciones al inicio y abrelo
	Dale a añadir y en la pestaña que se abre a continuacion pon un nombre, y en Orden escribe lo siguiente:
	- gnome-terminal -x sh -c "cd //RUTA/A/EJECUTABLE; ./EJECUTABLE"
	Con esto se ejecutara el programa que pongas al arrancar el equipo
