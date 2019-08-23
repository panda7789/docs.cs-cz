---
title: <serviceDiscovery>
ms.date: 03/30/2017
ms.assetid: a3c68a4a-fc95-43c5-aacb-785936c0cf39
ms.openlocfilehash: a99edd3a62a40c2efbc63a166b8c0b0d124e8a72
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936277"
---
# <a name="servicediscovery"></a>\<serviceDiscovery>
Určuje zjistitelnost koncových bodů služby.  
  
 \<system.ServiceModel>  
\<> chování  
\<serviceBehaviors>  
\<> chování  
\<serviceDiscovery>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceDiscovery>
        <announcementEndpoints>
          <endpoint name="String"
                    kind="Type" />
        </announcementEndpoints>
        <discoveryEndpoints>
          <endpoint name="String"
                    kind="Type" />
        </discoveryEndpoints>
      </serviceDiscovery>
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<announcementEndpoint >](announcementendpoint.md)|Kolekce koncových bodů oznámení V této části můžete zadat koncové body, které se mají použít pro posílání zpráv s oznámením.|  
|[\<discoveryEndpoint>](discoveryendpoint.md)|Kolekce koncových bodů zjišťování. V této části můžete zadat koncové body, na kterých se mají zprávy zjišťování naslouchat.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<> chování](behavior-of-endpointbehaviors.md)|Určuje chování element.|  
  
## <a name="remarks"></a>Poznámky  
 Po přidání do konfigurace chování služby tento prvek konfigurace zpřístupňuje všechny koncové body této služby. Funkce zjišťování těchto koncových bodů můžete dále konfigurovat pomocí [ \<](discoveryendpoint.md) podřízených elementů DiscoveryEndpoint > nebo [ \<announcementEndpoint >](announcementendpoint.md) . Pomocí části [> announcementEndpointmůžetenakonfigurovatoznámenízadánímkonfiguracekoncovéhobodu,kterásemápoužítkodesíláníoznámeníslužby(online/Helloaoffline/bye).\<](announcementendpoint.md) Pomocí části [> DiscoveryEndpointmůžeteručnězadatkoncovýbod,nakterémsemajízprávyzjišťovánínaslouchat.\<](discoveryendpoint.md)  
  
## <a name="example"></a>Příklad  
 Následující příklad konfigurace určuje, že CalculatorService bude zjistitelný a volitelně Určuje koncový bod oznámení, který se má použít.  
  
```xml  
<services>
  <service name="CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    ...
  </service>
</services>
<behaviors>
  <serviceBehaviors>
    <behavior name="CalculatorServiceBehavior">
      <serviceDiscovery>
        <announcementEndpoints>
          <endpoint name="udpEndpoint"
                    kind="udpAnnouncementEndpoint" />
        </announcementEndpoints>
      </serviceDiscovery>
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>
