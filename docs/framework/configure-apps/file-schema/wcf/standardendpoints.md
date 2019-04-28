---
title: <standardEndpoints>
ms.date: 03/30/2017
ms.assetid: d62153d7-a6e6-462a-a784-cca61e9c2ba1
ms.openlocfilehash: 66b86647689ea2ca39ae2f569d275aff1f48cba5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61757973"
---
# <a name="standardendpoints"></a>\<standardEndpoints>
Tento konfigurační oddíl umožňuje definovat kolekci standardních koncových bodů, které jsou opakovaně použitelnými koncovými body. Standardní koncový bod bude mít jednu nebo více adresa, vazba a kontrakt atributy nastavit na pevnou hodnotu. Například v koncový bod zjišťování vyřešen kontrakt. Standardní koncové body můžete použít také k rozšíření koncového bodu služby s novou vlastností k definování vlastních vazeb.  
  
 \<system.ServiceModel>  
  
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
|[\<announcementEndpoint>](announcementendpoint.md)|Definuje standardní koncový bod s pevným kontraktem oznámení. Službu můžete volitelně oznámit její dostupnost odesláním zprávu online a offline oznámení při otevření nebo zavření v uvedeném pořadí. Služba Windows Communication Foundation (WCF) určuje koncových bodů oznámení v [ \<serviceDiscovery >](servicediscovery.md) prvku a používá AnnouncementClient provádět oznámení. Klient přejí k naslouchání pro oznámení z jiné služby, ve skutečnosti funguje jako služba WCF; proto budete muset nakonfigurovat koncových bodů oznámení pro daného klienta v [ \<služby >](services.md) oddílu.|  
|[\<discoveryEndpoint>](discoveryendpoint.md)|Definuje standardní koncový bod s pevným kontraktem zjišťování. Po přidání do konfigurace služby, se určuje, kde naslouchat zprávám zjišťování. Po přidání do konfigurace klienta Určuje, kam má odesílat dotazy zjišťování.|  
|[\<dynamicEndpoint>](dynamicendpoint.md)|Tento prvek konfigurace definuje standardní koncový bod, který obsahuje informace, které umožní, aby aplikace fungovala jako klientský program, který může najít adresu koncového bodu dynamicky za běhu.|  
|[\<mexEndpoint>](mexendpoint.md)|Definuje standardní koncový bod s pevným kontraktem IMetadataExchange. Protože všechny koncové body metadat exchange určit jako jejich kontraktu IMetadataExchange, můžete použít tento standardní bod místo definování sami.|  
|[\<udpAnnouncementEndpoint>](udpannouncementendpoint.md)|Definuje standardní koncový bod, který používá služby pro odeslání zpráv oznámení UDP vazby. Má pevnou kontrakt a podporuje dvě verze zjišťování. Kromě toho má pevnou vazbou UDP a adresu výchozí hodnotu podle specifikace WS-Discovery (WS-Discovery dubna 2005 nebo verze 1.1 WS-Discovery). Můžete zadat adresu vícesměrového vysílání pro odesílání a příjem zpráv s oznámením.|  
|[\<udpDiscoveryEndpoint>](udpdiscoveryendpoint.md)|Definuje standardní koncový bod, který je předkonfigurován pro operace zjišťování přes UDP vazby vícesměrného vysílání. Tento koncový bod má pevnou kontrakt a podporuje dvě verze protokolu WS-Discovery. Kromě toho má pevnou vazbou UDP a adresu výchozí podle specifikace WS-Discovery (WS-Discovery dubna 2005 nebo V1.1 WS-Discovery).|  
|[\<webHttpEndpoint>](webhttpendpoint.md)|Definuje standardní koncový bod s pevnou [ \<webHttpBinding >](webhttpbinding.md) vazby, která automaticky přidá [ \<webHttp >](webhttp.md) chování. Při zápisu služby REST, používejte tento koncový bod.|  
|[\<webScriptEndpoint>](webscriptendpoint.md)|Definuje standardní koncový bod s pevnou [ \<webHttpBinding >](webhttpbinding.md) vazby, která automaticky přidá [ \<enableWebScript >](enablewebscript.md) chování. Používejte tento koncový bod, když vytváříte službu, která je volána z aplikace technologie ASP.NET AJAX.|  
|[\<workflowControlEndpoint>](workflowcontrolendpoint.md)|Definuje standardní koncový bod pro řízení spouštění instance pracovního postupu (vytvoření, spuštění, pozastavení, ukončit atd).|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|\<system.ServiceModel>|Kořenový element všechny elementy konfigurace WCF.|  
  
## <a name="see-also"></a>Viz také:

- [Standardní koncové body](../../../../../docs/framework/wcf/feature-details/standard-endpoints.md)
