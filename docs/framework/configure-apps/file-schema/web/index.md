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
ms.openlocfilehash: 030841330ff37cddb0c9e3e466a55a4be098e784
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088789"
---
# <a name="web-settings-schema"></a>Schéma nastavení webu
Webové nastavení určuje nastavení ASP.NET procesoru a na úrovni spuštění, které se vztahuje na chování v rámci procesu spravované vrstvou hostování ASP.NET. Tato nastavení se liší od nastavení aplikačního typu domény, které jsou uvedeny v souboru Web. config aplikace ASP.NET.  
  
Nastavení webu jsou obsažena v souborech ASPNET. config, které jsou umístěny v instalačních složkách pro verze .NET Framework. Například soubor ASPNET. config pro .NET Framework 2,0 je v následující složce:  
  
`C:\Windows\Microsoft.NET\Framework\v2.0.50727\`  
  
Webové nastavení se nepoužívá v žádné jiné konfigurační soubory, jako je například soubor Machine. config, kořenový soubor Web. config nebo Web. config na úrovni aplikace.  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.web>**](system-web-element-web-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<applicationPool>**](applicationpool-element-web-settings.md)

|Prvek|Description|  
|-------------|-----------------|  
|[\<system.web>](system-web-element-web-settings.md)|Obsahuje informace, které používá vrstva hostování ASP.NET.|  
|[\<applicationPool>](applicationpool-element-web-settings.md)|Určuje nastavení ASP.NET CPU a na úrovni spuštění, která se vztahují na chování v rámci procesu spravované vrstvou hostování ASP.NET.|  
  
## <a name="see-also"></a>Viz také

- [Schéma konfiguračního souboru](../index.md)
