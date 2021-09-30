#Proyecto de Big Data con Redshift

- **Primeros Pasos**
    - **¿Qué es un Data Warehouse?**
        - Es una base de datos que recibe información de muchas fuentes de datos.
        - Su objetivo es unificar la información para ayudar a la analítica de la empresa.
        - Se usa el proceso de ETL (extract, transform, load) para alimentar el Data Warehouse.
        - Extraer: Obtener los datos de las distintas bases de datos
        - Transformar: Realizar una limpieza y modificación de los datos, creando una buena estructura analítica.
        - Cargar: Luego de transformar los datos, se cargar al DW
        
        **¿Que es una estructura analítica?**
        
        Depende de la organización pero el estandar es el modelo dimensional, que posee:        
        - Tabla de hechos: Que quiero medir
        - Tabla de dimensiones: Como medirlo, es decir, que variables son importante para generar los análisis
        
        ![https://static.platzi.com/media/user_upload/db_multidimensional%20%281%29-040b6bdc-52fa-456a-bd4d-1753f689ee60.jpg](https://static.platzi.com/media/user_upload/db_multidimensional%20%281%29-040b6bdc-52fa-456a-bd4d-1753f689ee60.jpg)
        
        Otro ejemplo seria en una consulta médica, donde la tabla de hechos es la tabla de consultas.
        
        ![https://s3.us-west-2.amazonaws.com/secure.notion-static.com/2a850c2d-bfe8-4b6a-a9e7-b673066c910a/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210930%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210930T210547Z&X-Amz-Expires=86400&X-Amz-Signature=e793f67a368e3b816cb3a6d13b478e292a8aa7b36e1bdb7787177b5bcb3d87a8&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/2a850c2d-bfe8-4b6a-a9e7-b673066c910a/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210930%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210930T210547Z&X-Amz-Expires=86400&X-Amz-Signature=e793f67a368e3b816cb3a6d13b478e292a8aa7b36e1bdb7787177b5bcb3d87a8&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png)
        
        ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/11c37fb3-1665-44c0-ac85-8a74fa939808/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/11c37fb3-1665-44c0-ac85-8a74fa939808/Untitled.png)
        
        **Arquitectura del data warehouse**
        ● Tablas de hechos
        
        Contienen la información que queremos
        medir / analizar.
        
        ● Tablas de dimensiones
        
        Contienen la información del “cómo” lo
        quiero medir.
        
        ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/566724a6-0ecd-4813-93aa-a7ec1153af12/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/566724a6-0ecd-4813-93aa-a7ec1153af12/Untitled.png)
        
        El modelo que usaremos en Redshift:
        
    - **Bases de datos columnares y arquitectura orientada a optimización de consultas**
        - Base de datos relacional: Orientada a la alta transaccionalidad
        - Base de datos columnas: Orientada a la analítica
        
        Amazon Redshift es un servicio de almacén de datos completamente administrado, empresarial y de varios petabytes.
        
        Esta guía se centra en el uso de Amazon Redshift para crear y administrar un data warehouse. Si trabaja con bases de datos como diseñador, desarrollador de software o administrador, le proporciona la información que necesita para diseñar, desarrollar, hacer consultas y mantener el data warehouse.
        
        Excelentes para aplicaciones de analítica.
        ● En redshift cada columna se almacena en bloques de 1 MB.
        ● Una consulta a una tabla de 10 columnas de las cuales solo requiero 2, leería únicamente las 2 necesarias.
        
        Integración total con AWS.
        ● La base de datos más rápida en la nube.
        ● Los costos más bajos en la nube.
        ● Alta escalabilidad.
        ● Clientes SQL.
        
        Dbeaver: la usaremos para procesar nuestras DBs en redshift:
        
    - **¿Cómo funciona AWS Redshift?**
        
        El secreto es repartir el trabajo, no se instala en un único servidor sino que se instala en un clúster(arreglos de varios servidores conectados **NODOS**)
        
        **Nos conectamos a un nodo líder.**
        
        El cual organiza y asigna las tareas a los otros nodos. (Tareas en paralelos)El nodo seguidor
        
        Y cada nodo seguidor reparte su tarea entre sus Slides. Para trabajar la tarea asignada por el nodo lider en paralelo.
        
        La base de redshift es PostgreSQL.
        
        ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/294ed244-cfad-4379-b47e-591c685b5397/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/294ed244-cfad-4379-b47e-591c685b5397/Untitled.png)
        
        **Documentación:**
        
        [https://docs.aws.amazon.com/redshift/latest/dg/c_high_level_system_architecture.html](https://docs.aws.amazon.com/redshift/latest/dg/c_high_level_system_architecture.html)
