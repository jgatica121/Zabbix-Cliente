# Configuración de Nagstamon.

Para poder configurar Nagstamon debemos descargarlo desde la pagina el rpm o el ejecutable necesario dependiendo de nuestra distribución de S.O.

**URL: ** https://nagstamon.ifw-dresden.de/

Para la prueba que vamos a realizar, vamos a descargar el sigueinte paquete.

* nagstamon-3.4.1.fedora32-1.noarch.rpm

el cual vamos a instalar en nuestro S.O.


          [jgatica@localhost Descargas]$ sudo yum localinstall nagstamon-3.4.1.fedora32-1.noarch.rpm
          [sudo] password for jgatica: 
          Updating Subscription Management repositories.
          Unable to read consumer identity
          This system is not registered to Red Hat Subscription Management. You can use subscription-manager to register.
          Repository copr:copr.fedorainfracloud.org:dsommers:openvpn-beta is listed more than once in the configuration
          Última comprobación de caducidad de metadatos hecha hace 0:47:18, el jue 07 ene 2021 11:45:35.
          Dependencias resueltas.
          ===============================================================================================================================================================================================
           Paquete                                                 Arquitectura                         Versión                                         Repositorio                                 Tam.
          ===============================================================================================================================================================================================
          Instalando:
           nagstamon                                               noarch                               3.4.1.fedora32-1                                @commandline                               665 k
          Instalando dependencias:
           python3-jeepney                                         noarch                               0.4.3-1.fc32                                    fedora                                     4.7 M
           python3-kerberos                                        x86_64                               1.3.0-8.fc32                                    fedora                                      32 k
           python3-keyring                                         noarch                               21.5.0-1.fc32                                   updates                                     75 k
           python3-requests-kerberos                               noarch                               0.12.0-9.fc32                                   fedora                                      26 k
           python3-secretstorage                                   noarch                               3.2.0-1.fc32                                    updates                                     34 k

          Resumen de la transacción
          ===============================================================================================================================================================================================
          Instalar  6 Paquetes

          Tamaño total: 5.5 M
          Tamaño total de la descarga: 4.9 M
          Tamaño instalado: 11 M
          ¿Está de acuerdo [s/N]?: s
          Descargando paquetes:
          (1/5): python3-secretstorage-3.2.0-1.fc32.noarch.rpm                                                                                                           115 kB/s |  34 kB     00:00    
          (2/5): python3-keyring-21.5.0-1.fc32.noarch.rpm                                                                                                                218 kB/s |  75 kB     00:00    
          (3/5): python3-kerberos-1.3.0-8.fc32.x86_64.rpm                                                                                                                106 kB/s |  32 kB     00:00    
          (4/5): python3-requests-kerberos-0.12.0-9.fc32.noarch.rpm                                                                                                       84 kB/s |  26 kB     00:00    
          (5/5): python3-jeepney-0.4.3-1.fc32.noarch.rpm                                                                                                                 1.5 MB/s | 4.7 MB     00:03    
          -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
          Total                                                                                                                                                          1.2 MB/s | 4.9 MB     00:04     
          Ejecutando verificación de operación
          Verificación de operación exitosa.
          Ejecutando prueba de operaciones
          Prueba de operación exitosa.
          Ejecutando operación
            Preparando          :                                                                                                                                                                    1/1 
            Instalando          : python3-jeepney-0.4.3-1.fc32.noarch                                                                                                                                1/6 
            Instalando          : python3-secretstorage-3.2.0-1.fc32.noarch                                                                                                                          2/6 
            Instalando          : python3-keyring-21.5.0-1.fc32.noarch                                                                                                                               3/6 
            Instalando          : python3-kerberos-1.3.0-8.fc32.x86_64                                                                                                                               4/6 
            Instalando          : python3-requests-kerberos-0.12.0-9.fc32.noarch                                                                                                                     5/6 
            Instalando          : nagstamon-3.4.1.fedora32-1.noarch                                                                                                                                  6/6 
            Ejecutando scriptlet: nagstamon-3.4.1.fedora32-1.noarch                                                                                                                                  6/6 
          /sbin/ldconfig: /lib64/libdns.so.1112.0.1 no es un fichero ELF - tiene los bytes mágicos equivocados en el comienzo.

          /sbin/ldconfig: /lib64/libdns.so.1112 no es un fichero ELF - tiene los bytes mágicos equivocados en el comienzo.


            Verificando         : python3-keyring-21.5.0-1.fc32.noarch                                                                                                                               1/6 
            Verificando         : python3-secretstorage-3.2.0-1.fc32.noarch                                                                                                                          2/6 
            Verificando         : python3-jeepney-0.4.3-1.fc32.noarch                                                                                                                                3/6 
            Verificando         : python3-kerberos-1.3.0-8.fc32.x86_64                                                                                                                               4/6 
            Verificando         : python3-requests-kerberos-0.12.0-9.fc32.noarch                                                                                                                     5/6 
            Verificando         : nagstamon-3.4.1.fedora32-1.noarch                                                                                                                                  6/6 
          Installed products updated.

          Instalado:
            nagstamon-3.4.1.fedora32-1.noarch                    python3-jeepney-0.4.3-1.fc32.noarch             python3-kerberos-1.3.0-8.fc32.x86_64       python3-keyring-21.5.0-1.fc32.noarch      
            python3-requests-kerberos-0.12.0-9.fc32.noarch       python3-secretstorage-3.2.0-1.fc32.noarch      

          ¡Listo!
          [jgatica@localhost Descargas]$ 
