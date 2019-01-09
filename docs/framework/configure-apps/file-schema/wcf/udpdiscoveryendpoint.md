---
title: '&lt;UdpDiscoveryEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: 1f485329-2771-43bc-88de-df8f2faa3bb7
ms.openlocfilehash: 6508f73de7920a339e40284c86b0d1d649e7eabe
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145429"
---
# <a name="ltudpdiscoveryendpointgt"></a>&lt;UdpDiscoveryEndpoint&gt;
Tento prvek konfigurace definuje standardní koncový bod, který je předkonfigurován pro operace zjišťování přes UDP vazby vícesměrného vysílání. Tento koncový bod má pevnou kontrakt a podporuje dvě verze protokolu WS-Discovery. Kromě toho má pevnou vazbou UDP a adresu výchozí podle specifikace WS-Discovery (WS-Discovery dubna 2005 nebo V1.1 WS-Discovery).  
  
 \<system.ServiceModel>  
\<standardEndpoints >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <discoveryEndpoint>
      <standardEndpoint discoveryMode="Adhoc/Managed"
                        discoveryVersion="WSDiscovery11/WSDiscoveryApril2005"
                        maxResponseDelay="Timespan"
                        multicastAddress="Uri"
                        name="String" />
    </discoveryEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|discoveryMode|Řetězec, který určuje režim protokolu zjišťování. Platné hodnoty jsou "Ad hoc" a "Spravovaný". Ve spravovaném režimu protokol spoléhá na Proxy zjišťování, která slouží jako úložiště zjistitelné služby. Režimu ad hoc vyžaduje protokol UDP použití vícesměrového vysílání mechanismus pro vyhledání dostupných služeb. Tato hodnota je typu <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode>.|  
|DiscoveryVersion|Řetězec, který určuje jeden ze dvou verzí protokolu WS-Discovery. Platné hodnoty jsou WSDiscovery11 a WSDiscoveryApril2005. Tato hodnota je typu <xref:System.ServiceModel.Discovery.DiscoveryVersion>.|  
|maxResponseDelay|Časový interval hodnotu, která určuje maximální hodnotu zpoždění protokolu zjišťování bude čekat před odesláním některé zprávy, jako je například sběru dat nebo vyřešit shoda.<br /><br /> Pokud se všechny ProbeMatches odesílají ve stejnou dobu, může docházet k síti storm. Chcete-li tomu zabránit, ProbeMatches odesílají pomocí náhodného zpoždění mezi každou ProbeMatch. Náhodné zpoždění je v rozsahu od 0 do hodnoty nastavené v tomto atributu. Pokud tento atribut je nastaven na hodnotu 0, jsou odesílány zprávy ProbeMatches v těsné smyčce bez jakéhokoli zpoždění. V opačném případě případě odesílají zprávy ProbeMatches s některé náhodné zpoždění nepřekročí celkový čas potřebný k odeslání všech zpráv ProbeMatches maxResponseDelay. Tato hodnota platí pouze pro služby, se používají klienti.|  
|multicastAddress|Identifikátor Uri určující adresu vícesměrového vysílání pro odesílání a přijímání zpráv zjišťování. Výchozí hodnota je jako vyhovující specifikace protokolu adresu vícesměrového vysílání.|  
|`name`|Řetězec, který určuje název konfigurace standardního koncového bodu. Název se používá v `endpointConfiguration` atribut koncového bodu služby propojit s jeho konfigurace je standardní koncový bod.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<udpTransportSettings >](../../../../../docs/framework/configure-apps/file-schema/wcf/udptransportsettings.md)|Kolekce nastavení, která vám umožní nakonfigurovat přenos UDP pro koncový bod protokolu UDP.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<standardEndpoints >](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|Kolekce standardních koncových bodů, které jsou předem definované koncové body s jedním nebo více z jejich vlastností (adresu, vazbu, kontrakt) pevné.|  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje služby přes UDP naslouchání pro zjišťování zprávy vícesměrového vysílání přenosu.  
  
```xml  
<services>
  <service name="CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    <endpoint binding="basicHttpBinding"
              address="calculator"
              contract="ICalculatorService" />
    <endpoint name="DiscoveryEndpoint"
              kind="udpDiscoveryEndpoint" />
  </service>
  <standardEndpoints>
    <udpDiscoveryEndpoint>
      <standardEndpoint name="DiscoveryEndpoint"
                        version="WSDiscoveryApril2005" />
    </udpDiscoveryEndpoint>
  </standardEndpoints>
</services>
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>
