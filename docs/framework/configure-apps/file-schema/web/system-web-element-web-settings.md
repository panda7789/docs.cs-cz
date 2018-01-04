---
title: "&lt;System.Web&gt; – Element (webové nastavení)"
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
- system.Web element
- <system.Web> element
- ASP.NET configuration system
- configuration files [ASP.NET]
ms.assetid: 24c4cf4f-ad32-42b2-b040-8e4549e2855e
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 59899178fd9fc8da2334883ed62d9f8655eb335b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltsystemwebgt-element-web-settings"></a>&lt;System.Web&gt; – Element (webové nastavení)
Obsahuje informace o správě procesy chování vrstvě hostování technologie ASP.NET.  
  
 \<Konfigurace >  
\<System.Web > elementu (webové nastavení)  
  
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
|[\<applicationPool >](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)|Určuje nastavení konfigurace pro fondy aplikací služby IIS v soubor aspnet.config.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Konfigurace >](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|Určuje kořenový element v každém konfiguračním souboru, který je používán modul common language runtime a [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] aplikace.|  
  
## <a name="remarks"></a>Poznámky  
 `system.web` Elementu a jeho podřízené `applicationPool` element byly přidány do [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] od [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)]. Při spuštění [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] nebo novější verze v integrovaném režimu, tato kombinace element vám umožní nakonfigurovat jak ASP.NET spravuje vláken a jak ho fronty požadavků při ASP.NET je hostovaná ve fondu aplikací služby IIS. Pokud spustíte [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] nebo novější verze v režimu Classic nebo ISAPI, tato nastavení ignorují.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak nakonfigurovat chování procesy ASP.NET v souboru aspnet.config, pokud technologie ASP.NET je hostovaná ve fondu aplikací služby IIS. Příklad předpokládá, že je služba IIS spuštěna v integrovaném režimu a zda je aplikace pomocí [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)] nebo novější. Toto chování se nevyskytuje ve verzích [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] starší než [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)]. Hodnoty v příkladu jsou výchozí hodnoty.  
  
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
|Ověření souboru||  
|Může být prázdný||  
  
## <a name="see-also"></a>Viz také  
 [\<applicationPool > – Element (webové nastavení)](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)
