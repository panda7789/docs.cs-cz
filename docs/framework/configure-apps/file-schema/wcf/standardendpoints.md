---
title: '&lt;standardEndpoints&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d62153d7-a6e6-462a-a784-cca61e9c2ba1
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7e0e13dd8a5ac35f47e258d2a49d65c32e8c91f1
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltstandardendpointsgt"></a>&lt;standardEndpoints&gt;
Tento konfigurační oddíl umožňuje definovat kolekce standardních koncových bodů, které jsou opakovaně použitelné předem nakonfigurované koncové body. Koncový bod standardní bude mít jeden nebo více adresy, vazby a atributy kontrakt nastavte na pevnou hodnotu. Například v koncový bod zjišťování vyřešen kontrakt. Standardní koncové body můžete taky rozšířit koncový bod služby s nové vlastnosti podobná definování vlastní vazby.  
  
 \<systém. ServiceModel >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.serviceModel>  
    <standardEndpoints>  
    </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<announcementEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md)|Definuje standardní koncový bod s pevnou oznámení kontrakt. Služba může volitelně informovat jeho dostupnost zaslat e online a offline oznámení, pokud je otevřen nebo uzavřený v uvedeném pořadí. A [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] služby určuje koncových bodů oznámení v [ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) elementu a používá AnnouncementClient k provedení hlášení. Chtějí naslouchat pro oznámení z jiné služby skutečně funguje jako klient [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] služba; proto budete muset nakonfigurovat koncových bodů oznámení pro daného klienta v [ \<služby >](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md) části.|  
|[\<discoveryEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md)|Definuje standardní koncový bod s pevnou zjišťování kontrakt. Při přidání konfigurace služby, určuje, kde přijímat zprávy zjišťování. Po přidání do konfigurace klienta Určuje, kam má posílat dotazy zjišťování.|  
|[\<dynamicEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/dynamicendpoint.md)|Tento element konfigurace definuje standardní koncový bod, který obsahuje informace o povolení aplikace fungovat jako klient programu, můžete najít adresa koncového bodu dynamicky za běhu.|  
|[\<mexEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/mexendpoint.md)|Definuje standardní koncový bod s pevnou IMetadataExchange kontrakt. Vzhledem k tomu, že všechny koncové body metadat serveru exchange zadejte IMetadataExchange jako jejich kontrakt, můžete použít tento standardní bod místo definování jeden pro sami.|  
|[\<udpAnnoucementEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/udpannoucementendpoint.md)|Definuje standardní koncový bod, který je používán služby pro odeslání zpráv oznámení vazbu UDP. Má pevnou kontraktu a podporuje dvě verze zjišťování. Kromě toho má vazbu pevné UDP a adresu výchozí hodnotu podle specifikace WS-Discovery (WS-Discovery. dubna 2005 nebo WS-Discovery verze 1.1). Můžete zadat adresu vícesměrového vysílání pro odesílání a přijímání zpráv oznámení.|  
|[\<udpDiscoveryEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/udpdiscoveryendpoint.md)|Definuje standardní koncový bod, který je předem nakonfigurovaný pro operace zjišťování přes UDP vícesměrového vysílání vazby. Tento koncový bod má pevnou kontraktu a podporuje dvě verze protokolu WS-Discovery. Kromě toho má pevnou vazba UDP a výchozí adresu podle specifikace WS-Discovery (WS-Discovery. dubna 2005 nebo V1.1 WS-Discovery).|  
|[\<webHttpEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpendpoint.md)|Definuje standardní koncový bod s pevným [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) vazby, který automaticky přidá [ \<webHttp >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) chování. Při zápisu služby REST, použijte tento koncový bod.|  
|[\<webScriptEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/webscriptendpoint.md)|Definuje standardní koncový bod s pevným [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) vazby, který automaticky přidá [ \<enableWebScript >](../../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) chování. Když vytváříte službu, která je volána z aplikace ASP.NET AJAX, použijte tento koncový bod.|  
|[\<workflowControlEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/workflowcontrolendpoint.md)|Definuje standardní koncový bod pro řízení provádění instancí pracovního postupu (vytvoření, spuštění, pozastavení, ukončit, atd).|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|\<systém. ServiceModel >|Kořenový element všechny konfigurační prvky WCF.|  
  
## <a name="see-also"></a>Viz také  
 [Standardní koncové body](../../../../../docs/framework/wcf/feature-details/standard-endpoints.md)
