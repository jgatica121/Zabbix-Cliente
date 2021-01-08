# Configuración de alerta de SELinux 

Para poder monitorear el estado de SELinux vamos hacerlo utilizando parámetros que configuraremos en archivos que se encuentran en el directorio.

* **/etc/zabbix/zabbix_agentd.d**

Vamos a crear el siguiente archivo  **userparameter_selinux.conf** el cual vamos a llenar con el siguiente contenido:

    UserParameter=selinux-enabled, [ "$(getenforce)" = "Enforcing" ] && echo 1 || echo 0

Validamos el estado de SELinux.

    [root@zabbix-04 zabbix_agentd.d]# getenforce 
    Enforcing
    
Colocamos SELinux en modo permisivo y validamos.
    
    [root@zabbix-04 zabbix_agentd.d]# setenforce 0
    [root@zabbix-04 zabbix_agentd.d]# getenforce 
    Permissive

Agregamos el siguiente booleano a nuestro servidor, para que la actualización se realice de manera correcta.

    [root@zabbix-04 zabbix_agentd.d]# semanage permissive zabbix_agent_t
    
    
## Configuración consola web Zabbix para realizar el monitoreo.

Para realizar la configuración de nuestra nueva alerta debemos ir a nuestra consola web.    

* http://zabbix-server.ansible-labs.com/zabbix


### Crear template

1.- Cuando nos encontremos dentro nos dirigimos a **Configuration** y sobre **Templates**

2.- Vamos a dar clic sobre **Create template**

3.- Llenamos los datos de la siguiente manera:

* Template name: Template-Linux-SELinux
* Visible name: Template-Linux-SELinux
* Groups: Templates/Operating systems

4.- Damos clic en **Add**

### Crear Applications 

1.- Ahora que tenemos creado nuestro template vamos a dar clic sobre su nombre.

2.- Vamos a ir al apartado de **Applications**

3.- Damos clic en **Create application**

4.- Llenamos los datos de la siguiente manera:

* Name: SELinux
 
5.- Damos clic en **Add**

### Crear Items

1.- Ahora que tenemos creado nuestro template vamos a dar clic sobre su nombre.

2.- Vamos a ir al apartado de **Items**

3.- Damos clic en **Create item**

4.- Llenamos los datos de la siguiente manera:

* Name: SELinux-is-enabled
* Type: Zabbix agent
* Key: selinux-enabled
* Update interval: 15s
* Show value: Service state
* Applications: SELinux

5.- Damos clic en **Add**

### Crear Triggers

1.- Ahora que tenemos creado nuestro template vamos a dar clic sobre su nombre.

2.- Vamos a ir al apartado de **Triggers**

3.- Damos clic en **Create Trigger**

4.- Llenamos los datos de la siguiente manera:

* Name: SELinux on {HOST.NAME} is disable
* Severity: Average
* Expression: {Template-Linux-SELinux:selinux-enabled.last()}=0

5.- Damos clic en **Add**

Ahora agregamos el template a nuestros clientes y realimos pruebas, si nuestro SELinux se encuentra en modo permissive mandara una alerta por correo electro y se alertara dentro del dashboard.
