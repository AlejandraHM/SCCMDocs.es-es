---
title: Compatibilidad con Windows 10
titleSuffix: Configuration Manager
description: Obtenga información sobre las versiones de Windows 10 que se admiten como clientes o para OSD con System Center Configuration Manager.
ms.date: 11/27/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: a1626a65-da22-49e0-9564-d2f752ea3f4b
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: a02f904614e245a61e533164d25c0280e3a4d486
ms.sourcegitcommit: 6e42785c8c26e3c75bf59d3df7802194551f58e1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/28/2018
ms.locfileid: "52456147"
---
# <a name="support-for-windows-10-in-configuration-manager"></a>Compatibilidad con Windows 10 en Configuration Manager  

*Se aplica a: System Center Configuration Manager (Rama actual)*


Obtenga información sobre las versiones de Windows 10 que admite Configuration Manager, incluidas:
 -  [Windows 10 como cliente de Configuration Manager](#windows-10-as-a-client)
 -  [Windows Assessment and Deployment Kit (ADK) para Windows 10](#windows-10-adk)

> [!Tip]
> Las compilaciones de Windows Server como cliente se admiten del mismo modo que la versión de Windows 10 asociada. Por ejemplo, Windows Server 2016 es la misma versión de compilación que Windows 10 LTSB 2016 y Windows Server versión 1803 es la misma versión de compilación que Windows 10 versión 1803.
> 
> Para más información sobre Windows Server como sistema de sitios, vea [Sistemas operativos compatibles con servidores de sistema de sitio de Configuration Manager](/sccm/core/plan-design/configs/supported-operating-systems-for-site-system-servers#the-server-core-installation-of-windows-server-version-1803).



## <a name="windows-10-as-a-client"></a>Windows 10 como cliente

Configuration Manager intenta proporcionar compatibilidad como cliente para cada versión nueva de Windows 10 tan pronto como es posible después de que se encuentre disponible. Como los productos tienen programaciones independientes de lanzamiento y desarrollo, la compatibilidad que Configuration Manager proporciona depende de cuándo se encuentra disponible cada una.

Una versión de Configuration Manager se quitará de la matriz después de que finalice la [compatibilidad con esa versión](/sccm/core/servers/manage/current-branch-versions-supported). De forma similar, la compatibilidad con versiones de Windows 10 como Enterprise 2015 LTSB o 1511 se quitará de la matriz cuando se eliminen del soporte técnico.

-   La última versión de la rama actual de Configuration Manager recibe las actualizaciones críticas y de seguridad, que pueden incluir correcciones para problemas con versiones de Windows 10. Cuando Microsoft publica una nueva versión de la rama actual de Configuration Manager, las versiones anteriores solo reciben actualizaciones de seguridad. Para más información, vea [Compatibilidad con versiones de la rama actual de System Center Configuration Manager](/sccm/core/servers/manage/current-branch-versions-supported).  

    > [!Note]  
    > La mejor manera de tener Windows 10 actualizado es estar al día con Configuration Manager. Para saber más, vea [Configuration Manager y Windows como servicio](/sccm/core/understand/configuration-manager-and-windows-as-service).  

-   Esta información complementa a [Sistemas operativos compatibles con dispositivos y clientes](/sccm/core/plan-design/configs/supported-operating-systems-for-clients-and-devices).  

-   Si usa la rama de mantenimiento a largo plazo de Configuration Manager, vea [Configuraciones admitidas para la rama de mantenimiento a largo plazo](/sccm/core/understand/supported-configurations-for-ltsb).  

<br/>
En la tabla siguiente se enumeran las versiones de Windows 10 que puede usar como cliente con diferentes versiones de Configuration Manager.

| Versión de Windows 10 | Configuration Manager 1710 | Configuration Manager 1802 | Configuration Manager 1806 | Configuration Manager 1810 |
|---------------------|-----|-----|-----|-----|
| Enterprise 2015 LTSB <!--10/14/2025-->   | ![Compatible.](media/green_check.png) | ![Compatible.](media/green_check.png) | ![Compatible.](media/green_check.png) | ![Compatible.](media/green_check.png) |
| Enterprise 2016 LTSB <!--10/13/2026-->   | ![Compatible.](media/green_check.png) | ![Compatible.](media/green_check.png) | ![Compatible.](media/green_check.png) | ![Compatible.](media/green_check.png) |
| Enterprise LTSC 2019 <!--10/10/2028-->   | ![No compatible](media/Red_X.png)   | ![No compatible](media/Red_X.png)   | ![Compatible.](media/green_check.png) | ![Compatible.](media/green_check.png) |
| 1607   <!--04/09/2019-->   | ![Compatible.](media/green_check.png) | ![Compatible.](media/green_check.png) | ![Compatible.](media/green_check.png) | ![Compatible.](media/green_check.png) |
| 1703   <!--10/08/2019-->   | ![Compatible.](media/green_check.png) | ![Compatible.](media/green_check.png) | ![Compatible.](media/green_check.png) | ![Compatible.](media/green_check.png) |
| 1709   <!--04/14/2020-->   | ![Compatible.](media/green_check.png) | ![Compatible.](media/green_check.png) | ![Compatible.](media/green_check.png) | ![Compatible.](media/green_check.png) |
| 1803   <!--11/10/2020-->   | ![No compatible](media/Red_X.png) | ![Compatible.](media/green_check.png) | ![Compatible.](media/green_check.png) | ![Compatible.](media/green_check.png) |
| 1809   <!--04/12/2021?-->   | ![No compatible](media/Red_X.png) | ![No compatible](media/Red_X.png) | ![Compatible.](media/green_check.png) | ![Compatible.](media/green_check.png) |

<!-- lifecycle reference: https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet -->

> [!Note]  
> La compatibilidad con versiones de canal semestrales de Windows 10 incluye las siguientes ediciones: Enterprise, Pro, Education y Pro Education.   

| Clave |
|--|
| ![Compatible](media/green_check.png) = **Compatible**  |
| ![No compatible](media/Red_X.png) = **Not supported** |

 > [!NOTE]  
 > A partir de la versión 1802, Configuration Manager es compatible con el cliente en dispositivos ARM64 de Windows 10. Las características de administración de cliente existentes deben funcionar con estos nuevos dispositivos. Por ejemplo, el inventario de hardware y software, las actualizaciones de software y la administración de aplicaciones. La implementación de SO no se admite actualmente. <!-- 1353704 --> 

Para más información sobre el ciclo de vida de Windows, vea [Hoja de datos del ciclo de vida de Windows](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet).



## <a name="windows-10-adk"></a>Windows 10 ADK

Cuando se implementan sistemas operativos con Configuration Manager, Windows ADK es una dependencia externa necesaria. Para más información, vea [Requisitos de infraestructura para la implementación de SO en Configuration Manager](/sccm/osd/plan-design/infrastructure-requirements-for-operating-system-deployment#windows-adk-for-windows-10).

En la tabla siguiente se enumeran las versiones de Windows 10 ADK que puede usar con diferentes versiones de Configuration Manager.

| Versión del ADK de Windows 10  | Configuration Manager 1710 | Configuration Manager 1802 | Configuration Manager 1806 | Configuration Manager 1810 |
|--------------------|-----|-----|-----|-----|
| 1703  | ![Compatible con versiones anteriores](media/blue_compat.png) | ![Compatible con versiones anteriores](media/blue_compat.png) | ![No compatible](media/Red_X.png) | ![No compatible](media/Red_X.png) |
| 1709  | ![Compatible.](media/green_check.png) | ![Compatible.](media/green_check.png) | ![Compatible con versiones anteriores](media/blue_compat.png) | ![No compatible](media/Red_X.png)   |
| 1803  | ![No compatible](media/Red_X.png) | ![Compatible.](media/green_check.png) | ![Compatible.](media/green_check.png) | ![Compatible con versiones anteriores](media/blue_compat.png) |
| 1809  | ![No compatible](media/Red_X.png) | ![No compatible](media/Red_X.png) | ![Compatible.](media/green_check.png) | ![Compatible.](media/green_check.png) |

|Clave|
|--|
| ![Compatible](media/green_check.png) = **Compatible** <br/> Microsoft recomienda el uso de la versión de Windows ADK que coincida con la de Windows que va a implementar. Por ejemplo, use la versión 1703 de Windows ADK para Windows 10 al implementar Windows 10 versión 1703. Para obtener más información sobre la compatibilidad del componente Windows ADK, consulte [DISM supported platforms](https://docs.microsoft.com/windows-hardware/manufacture/desktop/dism-supported-platforms) (Plataformas compatibles con DISM) y [USMT requirements](https://docs.microsoft.com/windows/deployment/usmt/usmt-requirements#bkmk-1) (Requisitos de USMT). |
| ![Compatible con versiones anteriores](media/blue_compat.png)  = **Compatible con versiones anteriores** <br/> Esta combinación no se ha probado pero debería funcionar. Informaremos de cualquier problema conocido o advertencia. |
| ![No compatible](media/Red_X.png) = **Not supported** |

 > [!Note]  
 > Configuration Manager solo admite componentes x86 y amd64 de Windows 10 ADK. Actualmente no admite componentes ARM o ARM64. 

> [!Tip]
> Las compilaciones de Windows Server tienen el mismo requisito de Windows ADK que la versión de Windows 10 asociada. Por ejemplo, Windows Server 2016 es la misma versión de compilación que Windows 10 LTSB 2016.
