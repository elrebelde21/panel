[![Logo Image](https://i.imgur.com/rrp2f0j.png)](https://panel.pyro.host)

<p align="center">
 <a aria-label="Pyro logo" href="https://pyro.host"><img src="https://i.imgur.com/uvIy6cI.png"></a>
 <a aria-label="Join the Pyro community on Discord" href="https://discord.gg/fxeRFRbhQh?utm_source=githubreadme&utm_medium=readme&utm_campaign=OSSLAUNCH&utm_id=OSSLAUNCH"><img alt="" src="https://i.imgur.com/qSfKisV.png"></a>
 <a aria-label="Licensed under Business Source License 1.1" href="https://github.com/pyrohost/panel/blob/main/LICENSE"><img alt="" src="https://i.imgur.com/UrJMbDk.png"></a>
</p>

<h1 align="center">pyrodactyl por Host Inc.</h1>

pyrodactyl es el panel de administración del servidor de juegos basado en Pterodactyl que se centra en mejoras de rendimiento, una interfaz accesible y reinventada y una experiencia de desarrollador de primer nivel. Construye más rápido, compila en tamaños más pequeños: el pirodáctilo es el mejor pterodáctilo del mundo.

> [!NOTA]
> Pyro Host Inc. y sus empleados no están obligados a brindar soporte a los usuarios si esto nos impide activamente trabajar en nuestra plataforma.

[![Dashboard Image](https://pyro.host/img/panel1.jpg)](https://panel.pyro.host)

## Cambios de pterodáctilo de vainilla

- **Tamaños de paquetes más pequeños:** pyrodactyl se construye usando Vite, y una importante remodelación de la aplicación significa que el tamaño de descarga inicial de pyrodactyl ha terminado. **[170 veces más pequeño que las principales horquillas de pterodáctilo y Pelican](https://i.imgur.com/tKWLHhR.png)**
- **Tiempos de construcción más rápidos:** pyrodactyl completa las construcciones en milisegundos con el poder de Turbo. Las compilaciones en frío sin caché finalizan en **menos de 7 segundos**.
- **Tiempos de carga más rápidos:** los tiempos de carga de pyrodactyl son, en promedio, **[más de 16 veces más rápidos](https://i.imgur.com/28XxmMi.png)** than other closed-source Pterodactyl tenedores y pelícano. Una división y fragmentación de código más inteligente significa que las páginas que visita en el panel solo cargan los recursos necesarios según demanda. Un mejor almacenamiento en caché significa que todo es simplemente ágil.
- **Más seguro:** la arquitectura moderna de pyrodactyl significa que **los CVE más severos y fácilmente explotables simplemente no existen**. También hemos implementado controles de integridad y SRI para construcciones de producción.
- **Más accesible:** Pyro cree que los juegos deberían estar fácilmente disponibles para todos. pyrodactyl se construye teniendo en cuenta las últimas pautas de accesibilidad web. pyrodactyl es **completamente navegable mediante el teclado, incluso menús contextuales**, y los lectores de pantalla son fácilmente compatibles.
- **Más accesible:** la interfaz amigable y accesible de pyrodactyl significa que cualquiera puede ejecutar con confianza un servidor de juegos. [with Pyro](https://pyro.host).

[![Dashboard Image](https://pyro.host/img/panel3.jpg)](https://panel.pyro.host)

## Pirodáctilo corriendo

### Requisitos previos

- Última versión LTS de NodeJS
- Pnpm (`npm i -g pnpm`)
- Turbo (`pnpm i -g turbo`)
-Git

###Linux

Configurar pyrodactyl es muy sencillo en Linux. Siga la [documentación oficial de Pterodactyl](https://pterodactyl.io/community/installation) para su distribución hasta el punto en que necesite descargar el panel.

En lugar de descargar el panel oficial, siga los pasos a continuación para instalar pyrodactyl:

1. `git clone https://github.com/pyrohost/panel.git /var/www/pterodactyl`
2. `cd /var/www/pterodactyl`
3. `npm i`
4. `pnpm ship`

Continúe con el resto de la instalación como lo haría con el panel oficial.

### Windows

Actualmente no es posible ejecutar pyrodactyl en un **entorno de producción** en Windows debido a que las alas son incompatibles, pero estamos [actively working on a replacement](https://github.com/pyrohost/alerion). Si conoces un poco de Rust, ¡nos encantaría recibir tu ayuda!

## Desarrollo local en Windows

pyrodactyl es el primer panel Pterodactyl del mundo que se puede desarrollar y ejecutar localmente (con Wings) en máquinas Windows a través de [Vagrant](https://www.vagrantup.com/). Verifique que haya cumplido con los requisitos previos anteriores y luego siga los pasos a continuación.

1. Clonar el repositorio del panel de pirodactilo
2. Ejecute `npm i` para instalar todos los paquetes necesarios.
3. Ejecute `pnpm ship` para construir pirodactilo. Esto almacenará en caché los resultados de la compilación y cargará los mapas fuente en Sentry. Las compilaciones posteriores sin cambios de código finalizarán en milisegundos.
4. Ejecute "vagrant up". Esto configurará las alas y los servicios necesarios para ejecutar las bases de datos, los servicios y la aplicación de pyrodactyl. Este proceso podría tardar hasta 15 minutos.
5. Una vez que reciba un mensaje que dice "pyrodactyl ya está funcionando en localhost:3000", visite esa URL en su navegador e inicie sesión con las credenciales predeterminadas proporcionadas en su consola. **¡Es importante que utilices localhost para conectarte a pyrodactyl! Si usa 127.0.0.1, se encontrará con problemas de CORS y otros problemas que no se solucionarán.**
6. Visite localhost:3000/admin para aprovisionar su primer servidor en pyrodactyl.

### Notas sobre el desarrollo local en Windows

- Si tiene el servidor de desarrollo en ejecución (`pnpm dev`), se entregará una compilación de desarrollo de la aplicación en localhost:3000 con HMR. Si desea obtener una vista previa de una versión de producción de pyrodactyl, finalice el servidor de desarrollo y ejecute `pnpm ship`. Una vez que finalice, también se servirá en localhost:3000.

- Si está ejecutando el servidor de desarrollo o ha creado una versión de producción de pyrodactyl, pero la visita a localhost:3000 se bloquea permanentemente, asegúrese de no tener otras aplicaciones o juegos abiertos que puedan interferir con cualquiera de los puertos en Vagrantfile. Por ejemplo, Steam puede usar el puerto 8080 u otro servidor de desarrollo puede estar usando un puerto usado por pyrodactyl. Ejecute `vagrant reload` para volver a apuntar los puertos a su máquina virtual después de asegurarse de que no haya nada que la esté usando, e inténtelo de nuevo.

- Si recibe un mensaje como "Vagrant no pudo montar las carpetas compartidas de VirtualBox", [es posible que necesite instalar el complemento vbguest para VirtualBox](https://stackoverflow.com/a/48569055/11537010) with ` El complemento vagabundo instala vagrant-vbguest`. Si ya está instalado, ejecute `vagrant plugin update vagrant-vbguest`.

- Recomendamos configurar [Almacenamiento en caché remoto mediante turbo](https://turbo.build/repo/docs/core-concepts/remote-caching). Cuando ejecuta `pnpm ship` en su máquina de desarrollo local, sus resultados se almacenarán en caché y se cargarán, lo que le permitirá finalizar una compilación en su servidor de producción en milisegundos.

- No recomendamos utilizar Hyper-V como capa de virtualización. Si su instalación vagabunda le pide una contraseña, es porque usó Hyper-V. La contraseña será su contraseña de Windows.

> [! PRECAUCIÓN]
> No recomendamos instalar paquetes a través de pnpm. Aunque es completamente posible ejecutar y compilar pyrodactyl únicamente con pnpm, pnpm es incompatible con nuestra estrategia de fragmentación de compilación que permite que pyrodactyl se cargue tan rápidamente.

## Historia de las estrellas

<a href="https://star-history.com/#pyrohost/panel&Date">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://api.star-history.com/svg?repos=pyrohost/panel&type=Date&theme=dark" />
    <source media="(prefers-color-scheme: light)" srcset="https://api.star-history.com/svg?repos=pyrohost/panel&type=Date" />
    <img alt="Star History Chart" src="https://api.star-history.com/svg?repos=pyrohost/panel&type=Date" />
  </picture>
</a>

## Licencia

Pterodactyl® Copyright © 2015 - 2022 Dane Everitt y colaboradores.

pyrodactyl™ Copyright © 2024 Pyro Host Inc.

pyrodactyl™ tiene licencia de Pyro Host Inc. bajo la [Licencia disponible de fuente Pyro (PSAL)](https://github.com/pyrohost/legal/blob/main/licenses/PSAL.md). Su acceso y uso del contenido de este repositorio se rige por los términos de PSAL. Si no está de acuerdo con los términos de PSAL, no se le permite acceder ni utilizar el contenido disponible en este repositorio.
