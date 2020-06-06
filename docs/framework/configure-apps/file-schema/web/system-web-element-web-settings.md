---
title: Element <system.web> (nastavení webu)
ms.date: 03/30/2017
helpviewer_keywords:
- Web.config configuration file [ASP.NET]
- system.Web element
- <system.Web> element
- ASP.NET configuration system
- configuration files [ASP.NET]
ms.assetid: 24c4cf4f-ad32-42b2-b040-8e4549e2855e
ms.openlocfilehash: b37b05bdf90630251cbfcf86751243a3a8b77663
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152838"
---
# <a name="systemweb-element-web-settings"></a>Element \<system.web> (nastavení webu)
Obsahuje informace o tom, jak vrstva hostování ASP.NET spravuje chování v rámci procesu.  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<system.web>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.web>  
</system.web>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  

Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  

Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<applicationPool>](applicationpool-element-web-settings.md)|Určuje nastavení konfigurace pro fondy aplikací služby IIS v souboru ASPNET. config.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|Určuje kořenový element v každém konfiguračním souboru, který je používán modulem CLR (Common Language Runtime) a .NET Framework aplikacemi.|  
  
## <a name="remarks"></a>Poznámky  

`system.web`Prvek a jeho podřízený `applicationPool` prvek byly přidány do .NET Framework v .NET Framework 3,5 SP1. Když spustíte službu IIS 7,0 nebo novější verze v integrovaném režimu, tato kombinace prvků vám umožní nakonfigurovat, jak ASP.NET spravuje vlákna a jak se budou požadavky do fronty ASP.NET hostovat v fondu aplikací služby IIS. Pokud v klasickém režimu nebo v režimu rozhraní ISAPI spustíte službu IIS 7,0 nebo novější, budou tato nastavení ignorována.  
  
## <a name="example"></a>Příklad  

Následující příklad ukazuje, jak nakonfigurovat ASP.NET chování v rámci procesu v souboru ASPNET. config při hostování ASP.NET ve fondu aplikací služby IIS. V příkladu se předpokládá, že služba IIS běží v integrovaném režimu a že aplikace používá .NET Framework 3,5 SP1 nebo novější verzi. K tomuto chování nedochází ve verzích .NET Framework starších než .NET Framework 3,5 SP1. Hodnoty v příkladu jsou výchozími hodnotami.  
  
```xml  
<configuration>  
  <system.web>  
    <applicationPool
        maxConcurrentRequestsPerCPU="5000"
        maxConcurrentThreadsPerCPU="0"
        requestQueueLimit="5000" />  
  </system.web>  
</configuration>  
```  
  
## <a name="element-information"></a>Informace o elementu  
  
|||  
|-|-|  
|Obor názvů||  
|Název schématu||  
|Soubor ověření||  
|Může být prázdné||  
  
## <a name="see-also"></a>Viz také

- [\<applicationPool>– Element (nastavení webu)](applicationpool-element-web-settings.md)
