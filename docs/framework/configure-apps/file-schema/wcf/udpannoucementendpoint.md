---
title: '&lt;udpAnnoucementEndpoint&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5b3fa9c5-f372-4df9-a9d6-1e426063b721
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 73f4dd1374164a005c600b81dcf4fa558a57c803
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltudpannoucementendpointgt"></a>&lt;udpAnnoucementEndpoint&gt;
Tento element konfigurace definuje standardní koncový bod, který je používán služby pro odeslání zpráv oznámení vazbu UDP. Má pevnou kontraktu a podporuje dvě verze zjišťování. Kromě toho má vazbu pevné UDP a adresu výchozí hodnotu podle specifikace WS-Discovery (WS-Discovery. dubna 2005 nebo WS-Discovery verze 1.1). Můžete zadat adresu vícesměrového vysílání pro odesílání a přijímání zpráv oznámení.  
  
\<systém. ServiceModel >  
\<standardEndpoints >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <announcementEndpoint>
      <standardEndpoint discoveryVersion="WSDiscovery11/WSDiscoveryApril2005" 
                        maxAnnouncementDelay="Timespan"
                        multicastAddress="Uri"
                        name="String" />
    </announcementEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|discoveryVersion|Řetězec, který určuje jeden z dvě verze protokolu WS-Discovery. Platné hodnoty jsou WSDiscovery11 a WSDiscoveryApril2005. Tato hodnota je typu <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.|  
|maxAnnouncementDelay|Hodnota časového rozpětí, která určuje maximální hodnotu zpoždění protokol zjišťování bude čekat před odesláním zprávy Hello. Před odesláním zprávy vyčká na hodnotu náhodný čas mezi 0 a hodnota tohoto atributu. Tento atribut slouží k nastavení malé, náhodné zpoždění, aby se zabránilo zahlcení sítě, když síť prochází a všechny služby dostane zpět online ve stejnou dobu.|  
|multicastAddress|Identifikátor URI, který určuje adresu vícesměrového vysílání pro odesílání a přijímání zpráv zjišťování. Výchozí hodnota je jako vyhovující specifikace protokolu adresy vícesměrového vysílání.|  
|name|Řetězec, který určuje název konfigurace standardní koncového bodu. Název je používán `endpointConfiguration` atribut propojení koncový bod standardní konfiguraci koncového bodu služby.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<udpTransportSettings >](../../../../../docs/framework/configure-apps/file-schema/wcf/udptransportsettings.md)|Kolekce nastavení, která vám umožní nakonfigurovat přenosu UDP pro koncový bod UDP.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<standardEndpoints >](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|Kolekce standardních koncových bodů, které jsou předem definované koncových bodů s jedním nebo více jejich vlastnosti (adresy, vazby, kontrakt) pevné.|  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, klient naslouchání pro oznámení přes protokol UDP. přenos vícesměrového vysílání s výchozí adresa vícesměrového vysílání a UDP přenos vícesměrového vysílání se zadanou adresou vícesměrového vysílání.  
  
```xml  
<services>  
  <service name="ServiceAnnouncementListener">  
      <endpoint name="udpAnnouncementEndpointStandard"  
                kind="udpAnnouncementEndpoint"  
                bindingConfiguration="..." />  
      <endpoint name="udpAnnouncementEndpoint2"  
                kind="udpAnnouncementEndpoint"  
                endpointConfiguration="AnnouncementConfiguration3702"  
                bindingConfiguration="..." />  
...  
  </service>  
</services>  
<standardEndpoints>  
  <udpAnnouncementEndpoint>  
     <standardEndpoint name="AnnouncementConfiguration2"   
          version="WSDiscoveryApril2005"   
          multicastAddress="soap.udp://239.255.255.250:3703"/>          
  </udpAnnouncementEndpoint>  
</standardEndpoints>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>
