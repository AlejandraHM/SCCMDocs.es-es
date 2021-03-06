---
title: Administración de clientes Linux y UNIX
titleSuffix: Configuration Manager
description: Administre clientes en servidores Linux y UNIX en System Center Configuration Manager.
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 948664f2-239d-47a8-92fc-f8efeebd5796
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 43c7d4768e7da6af69422cce772665250d39764f
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/12/2019
ms.locfileid: "56138575"
---
# <a name="how-to-manage-clients-for-linux-and-unix-servers-in-system-center-configuration-manager"></a>Cómo administrar clientes para servidores Linux y UNIX en System Center Configuration Manager

*Se aplica a: System Center Configuration Manager (Rama actual)*

Cuando se administran los servidores Linux y UNIX con System Center Configuration Manager, se pueden configurar recopilaciones, ventanas de mantenimiento y configuraciones de cliente para ayudar a administrar los servidores. Además, aunque el cliente de Configuration Manager para Linux y UNIX no tiene una interfaz de usuario, puede forzar al cliente a sondear manualmente la directiva de cliente.

##  <a name="BKMK_CollectionsforLnU"></a> Colecciones de servidores Linux y UNIX  
 Use recopilaciones para administrar grupos de servidores Linux y UNIX de la misma forma que usa recopilaciones para administrar otros tipos de cliente. Las colecciones pueden ser de pertenencia directa o basadas en consultas. Estas últimas identifican los sistemas operativos cliente, las configuraciones de hardware u otros detalles sobre el cliente que se almacenan en la base de datos del sitio. Por ejemplo, puede usar colecciones que incluyan servidores Linux y UNIX para administrar la siguiente configuración:  

- Configuración de cliente  

- Implementaciones de software  

- Aplicar ventanas de mantenimiento  

  Antes de poder identificar un cliente Linux o UNIX por su sistema operativo o distribución, debe recopilar el [inventario de hardware](../../../core/clients/manage/inventory/hardware-inventory-for-linux-and-unix.md) desde el cliente.  

  La configuración de cliente predeterminada para el inventario de hardware incluye información sobre el sistema operativo del equipo de cliente. Puede usar la propiedad **Título** de la clase **Sistema operativo** para identificar el sistema operativo de un servidor Linux o UNIX.  

  Puede ver detalles sobre los equipos que ejecutan el cliente de Configuration Manager para Linux y UNIX en el nodo **Dispositivos** del área de trabajo **Activos y compatibilidad** en la consola de Configuration Manager. En el área de trabajo **Activos y compatibilidad** de la consola de Configuration Manager, puede ver el nombre del sistema operativo de cada equipo en la columna **Sistema operativo**.  

  De forma predeterminada, los servidores Linux y UNIX son miembros de la recopilación **Todos los sistemas** . Le recomendamos crear recopilaciones personalizadas que incluyan solo servidores Linux y UNIX, o un subconjunto de ellos. Las colecciones personalizadas permiten administrar operaciones como la implementación de software o la asignación de la configuración de cliente a grupos de equipos similares, de manera que pueda medir con precisión el éxito de una implementación.   

  Cuando cree una recopilación personalizada para servidores Linux y UNIX, incluya consultas de regla de pertenencia que contengan el atributo de título para el atributo de sistema operativo. Para obtener más información sobre la creación de recopilaciones, consulte [How to create collections in System Center Configuration Manager](../../../core/clients/manage/collections/create-collections.md) (Creación de recopilaciones en System Center Configuration Manager).  

##  <a name="BKMK_MaintenanceWindowsforLnU"></a> Ventanas de mantenimiento para servidores Linux y UNIX  
 El cliente de Configuration Manager para servidores de Linux y UNIX admite el uso de [ventanas de mantenimiento](../../../core/clients/manage/collections/use-maintenance-windows.md). Esta compatibilidad no se ha modificado para los clientes basados en Windows.  

##  <a name="BKMK_ClientSettingsforLnU"></a> Configuración de cliente para servidores Linux y UNIX  
 Puede [configurar las opciones de cliente](../../../core/clients/deploy/configure-client-settings.md) que se aplican a servidores Linux y UNIX de la misma manera que configura las opciones para otros clientes.  

 De forma predeterminada, la **Configuración predeterminada del agente cliente** se aplica a servidores Linux y UNIX. También puede crear opciones de configuración de cliente personalizadas e implementarlas en recopilaciones de clientes específicos.  

 No hay ninguna configuración de cliente adicional que se aplique solo a los clientes de Linux y UNIX. Sin embargo, hay configuración predeterminada de cliente que no se aplica a los clientes de Linux y UNIX. El cliente para Linux y UNIX solo aplica opciones de configuración para funciones que admita.  

 Por ejemplo, una configuración de dispositivo cliente personalizada que permita y configure la configuración de control remoto se ignorará por los servidores de Linux y UNIX, ya que el cliente de Linux y UNIX no admite el control remoto.  

##  <a name="BKMK_PolicyforLnU"></a> Directiva de equipo para servidores Linux y UNIX  
 El cliente para servidores Linux y UNIX sondea periódicamente en su sitio la directiva de equipo para obtener información sobre las configuraciones solicitadas y para comprobar las implementaciones.  

 También puede forzar al cliente en un servidor Linux o UNIX para que sondee inmediatamente la directiva de equipo. Para hacer esto, use las credenciales **raíz** en el servidor para ejecutar el comando siguiente: **/opt/microsoft/configmgr/bin/ccmexec -rs policy**  

 Los detalles sobre el sondeo de la directiva de equipo se escriben en el archivo de registro de cliente compartido **scxcm.log**.  

> [!NOTE]  
>  El cliente de Configuration Manager para Linux y UNIX nunca solicita ni procesa la directiva de usuario.  

##  <a name="BKMK_ManageLinuxCerts"></a> Cómo administrar certificados en el cliente para Linux y UNIX  
 Después de instalar el cliente para Linux y UNIX, puede usar la herramienta **certutil** para actualizar el cliente con un nuevo certificado PKI e importar una nueva lista de revocación de certificados (CRL). Al instalar el cliente para Linux y UNIX, esta herramienta se coloca en **/opt/microsoft/configmgr/bin/certutil**. 

 Para administrar certificados, en cada cliente ejecute certutil con una de las siguientes opciones:  

|Opción|Más información|  
|------------|----------------------|  
|importPFX|Use esta opción para especificar un certificado que reemplace el certificado que actualmente usa un cliente.<br /><br /> Cuando use **-importPFX**, también debe usar el parámetro de línea de comandos **–password** para proporcionar la contraseña asociada con el archivo PKCS #12.<br /><br /> Use **-rootcerts** para especificar los requisitos de certificado raíz adicionales.<br /><br /> Ejemplo: **certutil -importPFX &lt;ruta de acceso al certificado PKCS #12> -password &lt;contraseña del certificado\> [-rootcerts&lt;lista separada por comas de certificados>]**|  
|-importsitecert|Use esta opción para actualizar el servidor de sitio que firma el certificado que se encuentra en el servidor de administración.<br /><br /> Ejemplo: **certutil -importsitecert &lt;ruta de acceso al certificado DER\>**|  
|-importcrl|Use esta opción para actualizar la CRL en el cliente con una o varias rutas de archivos CRL.<br /><br /> Ejemplo: **certutil -importcrl &lt;rutas de acceso de archivos CRL separados por comas\>**|  
