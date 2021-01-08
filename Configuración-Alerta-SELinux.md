# Configuración de alerta de SELinux 

Para poder monitorear el estado de SELinux vamos hacerlo utilizando parametros dentro del siguiente directorio.

* **/etc/zabbix/zabbix_agentd.d**

Vamos a crear el siguiente archivo  **userparameter_selinux.conf** el cual vamos a llenar con el siguiente contenido:

    UserParameter=selinux-enabled, [ "$(getenforce)" = "Enforcing" ] && echo 1 || echo 0
