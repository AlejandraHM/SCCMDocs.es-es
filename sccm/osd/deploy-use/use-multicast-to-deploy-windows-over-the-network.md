---
title: Usar multidifusión para implementar Windows a través de la red
titleSuffix: Configuration Manager
description: Use multidifusión en su entorno de System Center Configuration Manager para que varios equipos puedan descargar simultáneamente la imagen de sistema operativo.
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: conceptual
ms.assetid: 4cafb7fc-380b-41b1-b83e-045aebfb7131
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: a256435c927c880363d20e6e52a22179a3271f3a
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/12/2019
ms.locfileid: "56142381"
---
# <a name="use-multicast-to-deploy-windows-over-the-network-with-system-center-configuration-manager"></a>Usar multidifusión para implementar Windows a través de la red con System Center Configuration Manager

*Se aplica a: System Center Configuration Manager (Rama actual)*

Multidifusión es un método de optimización de red que puede usar en el entorno de System Center Configuration Manager si es probable que varios clientes descarguen la misma imagen de sistema operativo al mismo tiempo. Cuando se usa multidifusión, varios equipos descargan la imagen de sistema operativo de forma simultánea a medida que el punto de distribución la reparte mediante multidifusión, en lugar de que el punto de distribución envíe una copia de los datos a cada cliente a través de una conexión separada.  

 Puede implementar sistemas operativos a través de la red mediante multidifusión en los siguientes escenarios de implementación de sistema operativo:  

- [Actualizar un equipo existente con una nueva versión de Windows](refresh-an-existing-computer-with-a-new-version-of-windows.md)  

- [Instalar una nueva versión de Windows en un equipo nuevo (sin sistema operativo)](install-new-windows-version-new-computer-bare-metal.md)  

  Complete los pasos de uno de los escenarios de implementación de sistema operativo y luego use las secciones siguientes para admitir la multidifusión.  

##  <a name="BKMK_Configure"></a> Configurar un punto de distribución para admitir la multidifusión  
 Antes de usar la multidifusión durante la implementación del sistema operativo, debe configurar un punto de distribución para admitir la multidifusión. Para obtener más información, consulte [Configure distribution points to support multicast](../get-started/prepare-site-system-roles-for-operating-system-deployments.md#BKMK_DPMulticast) (Configuración de puntos de distribución para admitir la multidifusión).  

## <a name="prepare-an-operating-system-image-for-multicast-deployments"></a>Preparar una imagen de sistema operativo para implementaciones de multidifusión  
 Para configurar el paquete de imagen de sistema operativo para admitir la multidifusión, consulte [Prepare the operating system image for multicast deployments](../get-started/manage-operating-system-images.md#BKMK_OSImageMulticast) (Preparar la imagen de sistema operativo para implementaciones de multidifusión).  

##  <a name="BKMK_Deploy"></a> Implementar la secuencia de tareas  
 Implemente el sistema operativo en una recopilación de destino. Para obtener más información, vea [Deploy a task sequence](manage-task-sequences-to-automate-tasks.md#BKMK_DeployTS).  
