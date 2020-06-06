---
title: <announcementEndpoint>
ms.date: 03/30/2017
ms.assetid: 034b7c69-a770-4502-8cef-38007bbcd025
ms.openlocfilehash: decaaa1cea5345ff971b16cbb20a85dd803a52d5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850294"
---
# \<announcementEndpoint>
Tento prvek konfigurace definuje standardní koncový bod s pevným kontraktem oznámení. Služba může volitelně oznámit svou dostupnost odesláním online nebo offline zprávy s oznámením, když je otevřený nebo uzavřený v uvedeném pořadí. Služba Windows Communication Foundation (WCF) určuje koncové body oznámení v [\<serviceDiscovery>](servicediscovery.md) elementu a k provádění oznámení používá AnnouncementClient. Klient, který chce naslouchat oznámením z jiné služby, ve skutečnosti funguje jako služba WCF; Proto musíte nakonfigurovat koncové body oznámení pro tohoto klienta v [\<services>](services.md) části.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<announcementEndpoint>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <announcementEndpoint>
      <standardEndpoint discoveryVersion="WSDiscovery11/WSDiscoveryApril2005"
                        maxAnnouncementDelay="Timespan"
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
|name|Řetězec, který určuje název konfigurace standardního koncového bodu. Název se používá v `endpointConfiguration` atributu koncového bodu služby k propojení standardního koncového bodu s jeho konfigurací.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|Kolekce standardních koncových bodů, které jsou předem definovanými koncovými body s jednou nebo více vlastnostmi (adresa, vazba, smlouva) opraveny.|  
  
## <a name="example"></a>Příklad  
 Následující příklad znázorňuje klienta, který přijímá zprávy s oznámeními přes protokol HTTP a PEERNET.  
  
```xml  
<services>
  <service name="ServiceAnnouncementListener">
    <endpoint name="httpAnnouncementEndpoint"
              kind="announcementEndpoint"
              binding="basicHttpBinding"
              address="announcements" />
    <endpoint name="peerNetAnnouncementEndpoint"
              kind="announcementEndpoint"
              binding="peerTcpBinding"
              address="net.p2p://discoveryMesh/multicast"
              bindingConfiguration="discoveryPeerTcpBindingConfig" />
  ...
  </service>
</services>

<standardEndpoints>
  <announcementEndpoint>
    <standardEndpoint name="httpAnnouncementEndpoint"
                      version="WSDiscoveryApril2005" />
    <standardEndpoint name="peerNetAnnouncementEndpoint"
                      version="WSDiscoveryApril2005" />
  </announcementEndpoint>
</standardEndpoints>
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>
