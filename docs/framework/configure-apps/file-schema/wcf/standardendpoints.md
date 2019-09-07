---
title: <standardEndpoints>
ms.date: 03/30/2017
ms.assetid: d62153d7-a6e6-462a-a784-cca61e9c2ba1
ms.openlocfilehash: 76a5303650c4e2b2887d29f511d3088c78b58fe2
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399517"
---
# <a name="standardendpoints"></a>\<Oddílu StandardEndpoints >
Tento konfigurační oddíl umožňuje definovat kolekci standardních koncových bodů, které jsou opakovaně použitelnými koncovými body. Standardní koncový bod bude mít jednu nebo víc atributů adresa, vazba a kontraktu nastavenou na pevnou hodnotu. Například ve koncovém bodě zjišťování je smlouva opravena. Pomocí standardních koncových bodů můžete také rozšířenit koncový bod služby s novými vlastnostmi podobnými definování vlastních vazeb.  
  
[ **\<> Konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<Oddílu StandardEndpoints >**  
  
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
|[\<announcementEndpoint >](announcementendpoint.md)|Definuje standardní koncový bod s pevným kontraktem oznámení. Služba může volitelně oznámit svou dostupnost odesláním online nebo offline zprávy s oznámením, když je otevřený nebo uzavřený v uvedeném pořadí. Služba Windows Communication Foundation (WCF) určuje koncové body oznámení v [ \<prvku > serviceDiscovery](servicediscovery.md) a k provádění oznámení používá AnnouncementClient. Klient, který chce naslouchat oznámením z jiné služby, ve skutečnosti funguje jako služba WCF; Proto je nutné nakonfigurovat koncové body oznámení pro tohoto klienta v [ \<části služby >](services.md) .|  
|[\<discoveryEndpoint>](discoveryendpoint.md)|Definuje standardní koncový bod s pevným kontraktem zjišťování. Po přidání do konfigurace služby určuje, kde naslouchat pro zprávy zjišťování. Po přidání do konfigurace klienta Určuje, kam se mají odesílat dotazy zjišťování.|  
|[\<dynamicEndpoint>](dynamicendpoint.md)|Tento prvek konfigurace definuje standardní koncový bod, který obsahuje informace, které umožní aplikaci fungovat jako klientský program, který může najít adresu koncového bodu dynamicky za běhu.|  
|[\<mexEndpoint>](mexendpoint.md)|Definuje standardní koncový bod s pevnou smlouvou IMetadataExchange. Vzhledem k tomu, že všechny koncové body výměny metadat určují jako kontrakt IMetadataExchange, můžete použít tento standardní bod, místo abyste ho nadefinovali sami.|  
|[\<udpAnnouncementEndpoint>](udpannouncementendpoint.md)|Definuje standardní koncový bod, který používají služby k posílání zpráv oznámení přes vazbu UDP. Má pevnou smlouvu a podporuje dvě verze zjišťování. Navíc má pevnou vazbu UDP a výchozí hodnotu adresy uvedené ve specifikacích WS-Discovery (WS-Discovery duben 2005 nebo WS-Discovery verze 1,1). Můžete zadat adresu vícesměrového vysílání, která se má použít pro odesílání a příjem zpráv s oznámením.|  
|[\<udpDiscoveryEndpoint>](udpdiscoveryendpoint.md)|Definuje standardní koncový bod, který je předem nakonfigurovaný pro operace zjišťování prostřednictvím vazby vícesměrového vysílání UDP. Tento koncový bod má pevný kontrakt a podporuje dvě verze protokolu WS-Discovery. Kromě toho má pevnou vazbu UDP a výchozí adresu uvedenou ve specifikacích WS-Discovery (WS-Discovery duben 2005 nebo WS-Discovery V 1.1).|  
|[\<webHttpEndpoint>](webhttpendpoint.md)|Definuje standardní koncový bod s pevnou [ \<vazbou WebHttpBinding >](webhttpbinding.md) [ \<, která automaticky přidá chování >u protokolu WebHttp](webhttp.md) . Tento koncový bod použijte při psaní služby REST.|  
|[\<webScriptEndpoint>](webscriptendpoint.md)|Definuje standardní koncový bod s pevnou [ \<vazbou WebHttpBinding >](webhttpbinding.md) [ \<](enablewebscript.md) , který automaticky přidá chování enableWebScript >. Tento koncový bod použijte při psaní služby, která se volá z aplikace ASP.NET AJAX.|  
|[\<workflowControlEndpoint>](workflowcontrolendpoint.md)|Definuje standardní koncový bod pro řízení spouštění instancí pracovního postupu (vytvořit, spustit, pozastavit, ukončit atd.).|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|\<system.ServiceModel>|Kořenový element všech elementů konfigurace služby WCF.|  
  
## <a name="see-also"></a>Viz také:

- [Standardní koncové body](../../../wcf/feature-details/standard-endpoints.md)
