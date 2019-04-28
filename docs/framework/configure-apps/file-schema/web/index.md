---
title: Schéma nastavení webu
ms.date: 03/30/2017
helpviewer_keywords:
- Web.config configuration file [ASP.NET]
- ASP.NET configuration system, Web settings schema
- schema Web settings
- Web settings, schema [ASP.NET]
- configuration files [ASP.NET]
- configuration schema [.NET Framework], Web settings
ms.assetid: ae1ac356-267d-4753-8d7a-7a04eb45a9be
ms.openlocfilehash: 1f0241b65c915dd5703ceea97dd5b07f88832003
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698484"
---
# <a name="web-settings-schema"></a>Schéma nastavení webu
Nastavení webu zadejte procesoru a úroveň spuštění ASP.NET nastavení platná pro celého procesu chování spravuje hostování vrstvy technologie ASP.NET. Tato nastavení se liší od nastavení typ domény aplikace, která jsou uvedeny v souboru Web.config aplikace technologie ASP.NET.  
  
 Nastavení webu jsou obsaženy v souborech Aspnet.config, které jsou umístěné ve složce instalace pro verzi rozhraní .NET Framework. Například soubor Aspnet.config pro [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] je v následující složce:  
  
 `C:\Windows\Microsoft.NET\Framework\v2.0.50727\`  
  
 Webové nastavení nepoužívají v žádné další konfigurační soubory, například souboru machine.config, kořenový soubor Web.config nebo souborech Web.config na úrovni aplikace.  
  
 [\<Konfigurace > – Element](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [\<System.Web > – Element (nastavení webu)](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)  
  
 [\<applicationPool > – Element (nastavení webu)](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<system.web>](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)|Obsahuje informace, které používá vrstvy hostování technologie ASP.NET.|  
|[\<applicationPool>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)|Určuje procesoru a úroveň spuštění ASP.NET nastavení platná pro celého procesu chování spravuje hostování vrstvy technologie ASP.NET.|  
  
## <a name="see-also"></a>Viz také:

- [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)
