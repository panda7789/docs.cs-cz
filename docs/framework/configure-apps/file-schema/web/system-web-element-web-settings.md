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
ms.openlocfilehash: 5c5c857d4494b6d78b819e56bae4213abc5e2035
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699095"
---
# <a name="systemweb-element-web-settings"></a>@no__t element -0system. Web > (nastavení webu)
Obsahuje informace o tom, jak vrstva hostování ASP.NET spravuje chování v rámci procesu.  
  
[ **@no__t – 2configuration >** ](../configuration-element.md)  
&nbsp; @ no__t-1 **@no__t -3system. web >**  
  
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
  
|Prvek|Popis|  
|-------------|-----------------|  
|[@no__t – 1applicationPool >](applicationpool-element-web-settings.md)|Určuje nastavení konfigurace pro fondy aplikací služby IIS v souboru ASPNET. config.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[@no__t – 1configuration >](../configuration-element.md)|Určuje kořenový element v každém konfiguračním souboru, který je používán modulem CLR (Common Language Runtime) a .NET Framework aplikacemi.|  
  
## <a name="remarks"></a>Poznámky  

Prvek `system.web` a jeho podřízený prvek `applicationPool` byl přidán do .NET Framework jako .NET Framework 3,5 SP1. Když spustíte službu IIS 7,0 nebo novější verze v integrovaném režimu, tato kombinace prvků vám umožní nakonfigurovat, jak ASP.NET spravuje vlákna a jak se budou požadavky do fronty ASP.NET hostovat v fondu aplikací služby IIS. Pokud v klasickém režimu nebo v režimu rozhraní ISAPI spustíte službu IIS 7,0 nebo novější, budou tato nastavení ignorována.  
  
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
  
## <a name="see-also"></a>Viz také:

- [@no__t – 1applicationPool > – element (nastavení webu)](applicationpool-element-web-settings.md)
