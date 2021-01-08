# Configuración de alerta de SELinux 

Para poder monitorear el estado de SELinux vamos hacerlo utilizando parámetros que configuraremos en archivos que se encuentran en el directorio.

* **/etc/zabbix/zabbix_agentd.d**

Vamos a crear el siguiente archivo  **userparameter_selinux.conf** el cual vamos a llenar con el siguiente contenido:

    UserParameter=selinux-enabled, [ "$(getenforce)" = "Enforcing" ] && echo 1 || echo 0

Validamos el estado de SELinux.

    [root@zabbix-04 zabbix_agentd.d]# getenforce 
    Enforcing

Agregamos el siguiente booleano a nuestro servidor, para que la actualización se realice de manera correcta.

    [root@zabbix-04 zabbix_agentd.d]# semanage permissive zabbix_agent_t
    
