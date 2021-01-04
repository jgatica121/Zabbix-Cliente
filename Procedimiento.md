# Agregar clientes a Servidor Zabbix.

Para poder agregar clientes a nuestro servidor Zabbix existen 4 formas diferentes de hacerlo para lo cual vamos a explicar cada una de ellas:

  * Forma manual
  * Utilizando encriptación
  * Utilizando opciones de HostMetadata
  * AutoRegister
  
  
## Proceso 1. (Agregarlo de forma manul).

Para iniciar con este proceso debemos tener creados nuestro clientes.

**Iniciamos sesión**

    [jgatica@localhost Descargas]$ ssh root@10.0.0.69
    root@10.0.0.69's password: 
    Last login: Mon Jan  4 14:50:53 2021 from 10.0.0.201

**Instalamos los repositorio de Zabbix**

     root@zabbix-04 ~]#  rpm -Uvh https://repo.zabbix.com/zabbix/5.0/rhel/7/x86_64/zabbix-release-5.0-1.el7.noarch.rpm
     Recuperando https://repo.zabbix.com/zabbix/5.0/rhel/7/x86_64/zabbix-release-5.0-1.el7.noarch.rpm
     advertencia:/var/tmp/rpm-tmp.uKAKbV: EncabezadoV4 RSA/SHA512 Signature, ID de clave a14fe591: NOKEY
     Preparando...                         ################################# [100%]
     Actualizando / instalando...
        1:zabbix-release-5.0-1.el7         ################################# [100%]
        
**Instalamos el agente**

      [root@zabbix-04 yum.repos.d]# yum install zabbix-agent
      Complementos cargados:enabled_repos_upload, package_upload, product-id, search-disabled-repos, subscription-manager, tracer_upload
      rhel-7-server-ansible-2.9-rpms                                                                                                                                          | 2.3 kB  00:00:00     
      rhel-7-server-extras-rpms                                                                                                                                               | 2.0 kB  00:00:00     
      rhel-7-server-optional-rpms                                                                                                                                             | 1.8 kB  00:00:00     
      rhel-7-server-rpms                                                                                                                                                      | 2.0 kB  00:00:00     
      rhel-7-server-satellite-tools-6.8-rpms                                                                                                                                  | 2.1 kB  00:00:00     
      zabbix                                                                                                                                                                  | 2.9 kB  00:00:00     
      zabbix-non-supported                                                                                                                                                    |  951 B  00:00:00     
      zabbix/x86_64/primary_db                                                                                                                                                |  58 kB  00:00:00     
      zabbix-non-supported/x86_64/primary                                                                                                                                     | 1.6 kB  00:00:00     
      zabbix-non-supported                                                                                                                                                                       4/4
      Resolviendo dependencias
      --> Ejecutando prueba de transacción
      ---> Paquete zabbix-agent.x86_64 0:5.0.7-1.el7 debe ser instalado
      --> Resolución de dependencias finalizada

      Dependencias resueltas

      ===============================================================================================================================================================================================
       Package                                          Arquitectura                               Versión                                          Repositorio                                Tamaño
      ===============================================================================================================================================================================================
      Instalando:
       zabbix-agent                                     x86_64                                     5.0.7-1.el7                                      zabbix                                     453 k

      Resumen de la transacción
      ===============================================================================================================================================================================================
      Instalar  1 Paquete

      Tamaño total de la descarga: 453 k
      Tamaño instalado: 1.8 M
      Is this ok [y/d/N]: y
      Downloading packages:
      advertencia:/var/cache/yum/x86_64/7Server/zabbix/packages/zabbix-agent-5.0.7-1.el7.x86_64.rpm: EncabezadoV4 RSA/SHA512 Signature, ID de clave a14fe591: NOKEY] 121 kB/s | 359 kB  00:00:00 ETA 
      No se ha instalado la llave pública de zabbix-agent-5.0.7-1.el7.x86_64.rpm 
      zabbix-agent-5.0.7-1.el7.x86_64.rpm                                                                                                                                     | 453 kB  00:00:01     
      Obteniendo clave desde file:///etc/pki/rpm-gpg/RPM-GPG-KEY-ZABBIX-A14FE591
      Importando llave GPG 0xA14FE591:
       Usuarioid  : "Zabbix LLC <packager@zabbix.com>"
       Huella       : a184 8f53 52d0 22b9 471d 83d0 082a b56b a14f e591
       Paquete    : zabbix-release-5.0-1.el7.noarch (installed)
       Desde      : /etc/pki/rpm-gpg/RPM-GPG-KEY-ZABBIX-A14FE591
      Está de acuerdo [s/N]:s
      Running transaction check
      Running transaction test
      Transaction test succeeded
      Running transaction
      Advertencia: Las bases de datos (RPMDB) han sido modificadas por un elemento ajeno a yum.
        Instalando    : zabbix-agent-5.0.7-1.el7.x86_64                                                                                                                                          1/1 
      Uploading Package Profile
      Complementos cargados:product-id, subscription-manager
      Complementos cargados:product-id, subscription-manager
      Uploading Tracer Profile
        Comprobando   : zabbix-agent-5.0.7-1.el7.x86_64                                                                                                                                          1/1 

      Instalado:
        zabbix-agent.x86_64 0:5.0.7-1.el7                                                                                                                                                            

      ¡Listo!
 

**Iniciar el servicio**

    [root@zabbix-04 yum.repos.d]# systemctl start zabbix-agent
    [root@zabbix-04 yum.repos.d]# systemctl enable zabbix-agent
    Created symlink from /etc/systemd/system/multi-user.target.wants/zabbix-agent.service to /usr/lib/systemd/system/zabbix-agent.service.
    
**Modificar el archivo de configuración**

Para realizar esta tarea se omiten los comentarios que contiene el archivo.

    PidFile=/var/run/zabbix/zabbix_agentd.pid
    LogFile=/var/log/zabbix/zabbix_agentd.log
    LogFileSize=0
    **Server=10.0.0.150**
    ListenPort=10050
    ServerActive=10.0.0.150
    Hostname=zabbix-04
    Include=/etc/zabbix/zabbix_agentd.d/*.conf



