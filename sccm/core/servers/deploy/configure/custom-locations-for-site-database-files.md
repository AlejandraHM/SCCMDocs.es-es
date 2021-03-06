---
title: Ubicaciones de archivo de base de datos personalizadas
titleSuffix: Configuration Manager
description: Obtenga información sobre cómo especificar ubicaciones personalizadas para archivos de base de datos de SQL Server.
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 500a9aa6-68aa-44eb-bf49-350c1314a697
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 597ce060dc1fb37f1cc827da3e1c059958a91163
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32332736"
---
# <a name="custom-locations-for-system-center-configuration-manager-site-database-files"></a>Ubicaciones personalizadas para archivos de base de datos del sitio de System Center Configuration Manager

*Se aplica a: System Center Configuration Manager (Rama actual)*

 System Center Configuration Manager es compatible con las ubicaciones personalizadas para archivos de base de datos de SQL Server.  

> [!NOTE]  
>  La opción de especificar ubicaciones de archivos no predeterminadas no está disponible cuando se usa un clúster de SQL Server.  

 **Durante la configuración** de un nuevo sitio principal o un sitio de administración central, puede hacer lo siguiente:  

-   **Especificar ubicaciones de archivo no predeterminadas para la base de datos del sitio**: el programa de instalación de Configuration Manager crea después la base de datos del sitio mediante el uso de esas ubicaciones.  

-   **Especificar el uso de una base de datos de SQL Server creada previamente que usa ubicaciones de archivo personalizadas**: el programa de instalación de Configuration Manager usa dicha base de datos creada previamente y sus ubicaciones de archivo preconfiguradas.  

**Después de la configuración**, puede cambiar la ubicación de los archivos de la base de datos del sitio. Para ello, es necesario detener el sitio y editar la ubicación de los archivos en SQL Server:  

-   En el servidor de sitio de Configuration Manager, detenga el servicio **SMS_Executive**.  

-   Use la documentación de su versión de SQL Server para obtener información sobre cómo mover una base de datos de usuario. Por ejemplo, si usa SQL Server 2014, vea [Mover bases de datos de usuario](https://technet.microsoft.com/library/ms345483\(v=sql.120\).aspx) en TechNet.  

-   Después de completar el movimiento de archivos de la base de datos, reinicie el servicio **SMS_Executive** en el servidor de sitio de Configuration Manager.  
