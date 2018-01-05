---
title: "Schéma nastavení webu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Web.config configuration file [ASP.NET]
- ASP.NET configuration system, Web settings schema
- schema Web settings
- Web settings, schema [ASP.NET]
- configuration files [ASP.NET]
- configuration schema [.NET Framework], Web settings
ms.assetid: ae1ac356-267d-4753-8d7a-7a04eb45a9be
caps.latest.revision: "6"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: a4ece61330fe8e41d9afb894791f9f9e36db35f2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="web-settings-schema"></a>Schéma nastavení webu
Nastavení webové zadejte procesoru a úroveň spuštění ASP.NET nastavení, které platí pro procesy chování spravované technologií ASP.NET, který je hostitelem vrstvy. Tato nastavení se liší od nastavení typ domény aplikace, které jsou určené v souboru Web.config aplikace technologie ASP.NET.  
  
 Nastavení webové jsou obsažené v Aspnet.config soubory, které jsou umístěny v instalačních složkách verze rozhraní .NET Framework. Například soubor Aspnet.config pro [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] je v následující složce:  
  
 `C:\Windows\Microsoft.NET\Framework\v2.0.50727\`  
  
 Nastavení webové nepoužívají v další konfigurační soubory například souboru machine.config, kořenový soubor Web.config nebo souborů Web.config úrovni aplikace.  
  
 [\<Konfigurace > elementu](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [\<System.Web > elementu (webové nastavení)](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)  
  
 [\<applicationPool > – Element (webové nastavení)](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<System.Web >](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)|Obsahuje informace, které používá ASP.NET hostování vrstvy.|  
|[\<applicationPool >](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)|Určuje procesoru a nastavení ASP.NET úroveň spuštění, které platí pro procesy chování spravované technologií ASP.NET, který je hostitelem vrstvy.|  
  
## <a name="see-also"></a>Viz také  
 [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)
