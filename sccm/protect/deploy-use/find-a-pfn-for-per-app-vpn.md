---
title: Buscar un nombre de familia de paquete (PFN) para VPN por aplicación
titleSuffix: Configuration Manager
description: Obtenga información sobre las dos maneras de buscar un nombre de familia de paquete para poder configurar una VPN por aplicación.
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology: configmgr-protect
ms.topic: conceptual
ms.assetid: 47118499-3d26-4c25-bfde-b129de7eaa59
author: aczechowski
manager: dougeby
ms.author: aaroncz
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6e578b0f7ff5cf228afa8221be66134fce15e55c
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 02/12/2019
ms.locfileid: "56136133"
---
# <a name="find-a-package-family-name-pfn-for-per-app-vpn"></a>Buscar un nombre de familia de paquete (PFN) para VPN por aplicación

*Se aplica a: System Center Configuration Manager (Rama actual)*


Hay dos maneras de buscar un PFN para poder configurar una VPN por aplicación.

## <a name="find-a-pfn-for-an-app-thats-installed-on-a-windows-10-computer"></a>Buscar un PFN para una aplicación que está instalada en un equipo Windows 10

Si la aplicación con la que trabaja ya está instalada en un equipo Windows 10, puede usar el cmdlet [Get-AppxPackage](https://technet.microsoft.com/library/hh856044.aspx) de PowerShell para obtener el PFN.

La sintaxis de Get-AppxPackage es la siguiente:

` Parameter Set: __AllParameterSets`
` Get-AppxPackage [[-Name] <String> ] [[-Publisher] <String> ] [-AllUsers] [-User <String> ] [ <CommonParameters>]`

> [!NOTE]
> Es posible que deba ejecutar PowerShell como administrador para poder recuperar el PFN.

Por ejemplo, para obtener información sobre todas las aplicaciones universales instaladas en el equipo, use `Get-AppxPackage`.

Para obtener información sobre una aplicación cuyo nombre conoce, o parte de él, use `Get-AppxPackage *<app_name>`. Observe el uso del carácter comodín, que resulta especialmente útil si no está seguro del nombre completo de la aplicación. Por ejemplo, para obtener información sobre OneNote, use `Get-AppxPackage *OneNote`.


Esta es la información que se recupera para OneNote:

`Name                   : Microsoft.Office.OneNote`

`Publisher              : CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US`

`Architecture           : X64`

`ResourceId             :`

`Version                : 17.6769.57631.0`

`PackageFullName        : Microsoft.Office.OneNote_17.6769.57631.0_x64__8wekyb3d8bbwe`

`InstallLocation        : C:\Program Files\WindowsApps`

`\Microsoft.Office.OneNote_17.6769.57631.0_x64__8wekyb3d8bbwe`

`IsFramework            : False`

**`PackageFamilyName      : Microsoft.Office.OneNote_8wekyb3d8bbwe`**

`PublisherId            : 8wekyb3d8bbwe`



## <a name="find-a-pfn-if-the-app-is-not-installed-on-a-computer"></a>Buscar un PFN si la aplicación no está instalada en un equipo

1.  Vaya a https://www.microsoft.com/en-us/store/apps
2.  En la barra de búsqueda, escriba el nombre de la aplicación. En nuestro ejemplo, busque OneNote.
3.  Haga clic en el vínculo de la aplicación. Observe que la dirección URL a la que tiene acceso contiene una serie de letras al final. En nuestro ejemplo, la dirección URL tiene el siguiente aspecto: `https://www.microsoft.com/en-us/store/apps/onenote/9wzdncrfhvjl`
4.  En otra pestaña, pegue la siguiente dirección URL, `https://bspmts.mp.microsoft.com/v1/public/catalog/Retail/Products/<app id>/applockerdata`, pero sustituya `<app id>` por el identificador de la aplicación que obtuvo en https://www.microsoft.com/en-us/store/apps, esa serie de letras del final de la dirección URL en el paso 3. En nuestro ejemplo de OneNote, pegaría lo siguiente: `https://bspmts.mp.microsoft.com/v1/public/catalog/Retail/Products/9wzdncrfhvjl/applockerdata`.

En Microsoft Edge, se muestra la información que le interesa. En Internet Explorer, debe hacer clic en **Abrir** para verla. El valor PFN se muestra en la primera línea. Este es el aspecto de los resultados de nuestro ejemplo:


`{`
`  "packageFamilyName": "Microsoft.Office.OneNote_8wekyb3d8bbwe",`
`  "packageIdentityName": "Microsoft.Office.OneNote",`
`  "windowsPhoneLegacyId": "ca05b3ab-f157-450c-8c49-a1f127f5e71d",`
`  "publisherCertificateName": "CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US"`
`}`
