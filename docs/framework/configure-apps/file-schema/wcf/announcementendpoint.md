---
title: '&lt;announcementEndpoint&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 034b7c69-a770-4502-8cef-38007bbcd025
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5458149a68273a62b1636dec0da4d9494fb63a99
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltannouncementendpointgt"></a>&lt;announcementEndpoint&gt;
Tento element konfigurace definuje standardní koncový bod s pevnou oznámení kontrakt. Služba může volitelně informovat jeho dostupnost zaslat e online a offline oznámení, pokud je otevřen nebo uzavřený v uvedeném pořadí. A [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] služby určuje koncových bodů oznámení v [ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) elementu a používá AnnouncementClient k provedení hlášení. Chtějí naslouchat pro oznámení z jiné služby skutečně funguje jako klient [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] služba; proto budete muset nakonfigurovat koncových bodů oznámení pro daného klienta v [ \<služby >](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md) části.  
  
\<systém. ServiceModel >  
\<standardEndpoints >  
  
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
|discoveryVersion|Řetězec, který určuje jeden z dvě verze protokolu WS-Discovery. Platné hodnoty jsou WSDiscovery11 a WSDiscoveryApril2005. Tato hodnota je typu <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.|  
|maxAnnouncementDelay|Hodnota časového rozpětí, která určuje maximální hodnotu zpoždění protokol zjišťování bude čekat před odesláním zprávy Hello. Před odesláním zprávy vyčká na hodnotu náhodný čas mezi 0 a hodnota tohoto atributu. Tento atribut slouží k nastavení malé, náhodné zpoždění, aby se zabránilo zahlcení sítě, když síť prochází a všechny služby dostane zpět online ve stejnou dobu.|  
|name|Řetězec, který určuje název konfigurace standardní koncového bodu. Název je používán `endpointConfiguration` atribut propojení koncový bod standardní konfiguraci koncového bodu služby.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<standardEndpoints >](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|Kolekce standardních koncových bodů, které jsou předem definované koncových bodů s jedním nebo více jejich vlastnosti (adresy, vazby, kontrakt) pevné.|  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje klienta prostřednictvím protokolu http a peernet naslouchání pro zprávy oznámení.  
  
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
 <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>
