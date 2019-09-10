---
title: <udpAnnouncementEndpoint>
ms.date: 03/30/2017
ms.assetid: 5b3fa9c5-f372-4df9-a9d6-1e426063b721
ms.openlocfilehash: 8dabf8845126705d082d080b643688ed62883f39
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854915"
---
# <a name="udpannouncementendpoint"></a>\<udpAnnouncementEndpoint >
Tento prvek konfigurace definuje standardní koncový bod, který používají služby k posílání zpráv oznámení přes vazbu UDP. Má pevnou smlouvu a podporuje dvě verze zjišťování. Navíc má pevnou vazbu UDP a výchozí hodnotu adresy uvedené ve specifikacích WS-Discovery (WS-Discovery duben 2005 nebo WS-Discovery verze 1,1). Můžete zadat adresu vícesměrového vysílání, která se má použít pro odesílání a příjem zpráv s oznámením.  
  
[ **\<> Konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Oddílu StandardEndpoints >** ](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<udpAnnouncementEndpoint >**  
  
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
|discoveryVersion|Řetězec, který určuje jednu ze dvou verzí protokolu WS-Discovery. Platné hodnoty jsou WSDiscovery11 a WSDiscoveryApril2005. Tato hodnota je typu <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.|  
|maxAnnouncementDelay|Hodnota TimeSpan, která určuje maximální hodnotu pro prodlevu, po kterou bude protokol zjišťování čekat před odesláním zprávy Hello. Zprávy budou čekat na hodnotu náhodného času mezi 0 a hodnotou tohoto atributu před odesláním. Tento atribut slouží k nastavení malé náhodné prodlevy, aby se zabránilo výpadkům sítě v případě, že dojde k vygenerování sítě, a všechny služby se vrátí zpět do režimu online ve stejnou dobu.|  
|multicastAddress|Identifikátor URI, který určuje adresu vícesměrového vysílání, která se má použít pro odesílání a příjem zpráv zjišťování. Výchozí hodnota je adresa vícesměrového vysílání, která odpovídá specifikaci protokolu.|  
|name|Řetězec, který určuje název konfigurace standardního koncového bodu. Název se používá v `endpointConfiguration` atributu koncového bodu služby k propojení standardního koncového bodu s jeho konfigurací.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<udpTransportSettings>](udptransportsettings.md)|Kolekce nastavení, která umožňují nakonfigurovat přenos UDP pro koncový bod UDP.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|Kolekce standardních koncových bodů, které jsou předem definovanými koncovými body s jednou nebo více vlastnostmi (adresa, vazba, smlouva) opraveny.|  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, že klient naslouchá oznámení prostřednictvím přenosu vícesměrového vysílání UDP s výchozí adresou vícesměrového vysílání a přenos vícesměrového vysílání UDP se zadanou adresou vícesměrového vysílání.  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>
