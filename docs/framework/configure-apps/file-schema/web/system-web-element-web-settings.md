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
ms.openlocfilehash: 3ffd25dae3826df0f02f2afb707f7317b2d92d24
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65584543"
---
# <a name="systemweb-element-web-settings"></a>\<System.Web > – Element (nastavení webu)
Obsahuje informace o jak spravuje chování v celém procesu vrstvy hostování technologie ASP.NET.  
  
 \<Konfigurace >  
\<System.Web > – Element (nastavení webu)  
  
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
|[\<applicationPool>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)|Určuje nastavení konfigurace pro fondy aplikací IIS v soubor aspnet.config.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<configuration>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|Určuje kořenový element v každém konfiguračním souboru, který je používán common language runtime a aplikace rozhraní .NET Framework.|  
  
## <a name="remarks"></a>Poznámky  
 `system.web` Elementu a jeho podřízené `applicationPool` element byly přidány do rozhraní .NET Framework počínaje verzí [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)]. Při spuštění [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] nebo novější verze v integrovaném režimu, tato kombinace elementu vám umožní nakonfigurovat jak spravuje vláken ASP.NET a jak se zařadí do fronty žádostí při technologie ASP.NET je hostovaná ve fondu aplikací služby IIS. Pokud spustíte [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] nebo novější verze v režimu Classic nebo rozhraní ISAPI, tato nastavení ignorují.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak konfigurovat chování v celém procesu ASP.NET v souboru aspnet.config technologie ASP.NET je hostovaná ve fondu aplikací služby IIS. Příklad předpokládá, že služba IIS pracuje v integrovaného režimu a že aplikace používá [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)] nebo novější. K tomuto chování nedojde ve verzích rozhraní .NET Framework starší než [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)]. Hodnoty v tomto příkladu jsou výchozí hodnoty.  
  
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
|Může být prázdné.||  
  
## <a name="see-also"></a>Viz také:

- [\<applicationPool > – Element (nastavení webu)](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)
