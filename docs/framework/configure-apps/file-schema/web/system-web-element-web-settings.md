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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152838"
---
# <a name="systemweb-element-web-settings"></a>\<system.web> Element (Nastavení webu)
Obsahuje informace o tom, jak ASP.NET hostitelské vrstvy spravuje chování celého procesu.  
  
[**\<>konfigurace**](../configuration-element.md)  
&nbsp;&nbsp;**\<system.web>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.web>  
</system.web>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  

Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  

Žádné.  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[\<aplikacePool>](applicationpool-element-web-settings.md)|Určuje nastavení konfigurace fondů aplikací služby IIS v souboru aspnet.config.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[\<>konfigurace](../configuration-element.md)|Určuje kořenový prvek v každém konfiguračním souboru, který používá aplikace COMMON Language runtime a .NET Framework.|  
  
## <a name="remarks"></a>Poznámky  

Prvek `system.web` a jeho `applicationPool` podřízený prvek byly přidány do rozhraní .NET Framework od rozhraní .NET Framework 3.5 SP1. Při spuštění služby IIS 7.0 nebo novějších verzí v integrovaném režimu umožňuje tato kombinace prvků konfigurovat způsob správy vláken ASP.NET a způsob, jakým zařazuje požadavky do fronty, když je ASP.NET hostován ve fondu aplikací služby IIS. Pokud spustíte službu IIS 7.0 nebo novější verze v klasickém režimu nebo režimu ISAPI, budou tato nastavení ignorována.  
  
## <a name="example"></a>Příklad  

Následující příklad ukazuje, jak nakonfigurovat ASP.NET chování celého procesu v souboru aspnet.config, když je ASP.NET hostováno ve fondu aplikací služby IIS. Příklad předpokládá, že službu IIS je spuštěna v integrovaném režimu a že aplikace používá rozhraní .NET Framework 3.5 SP1 nebo novější verzi. K tomuto chování nedochází ve verzích rozhraní .NET Framework starších než rozhraní .NET Framework 3.5 SP1. Hodnoty v příkladu jsou výchozí hodnoty.  
  
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
|Ověřovací soubor||  
|Může být prázdný||  
  
## <a name="see-also"></a>Viz také

- [\<applicationPool> Element (Nastavení webu)](applicationpool-element-web-settings.md)
