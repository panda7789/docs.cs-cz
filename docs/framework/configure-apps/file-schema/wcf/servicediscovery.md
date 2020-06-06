---
title: <serviceDiscovery>
ms.date: 03/30/2017
ms.assetid: a3c68a4a-fc95-43c5-aacb-785936c0cf39
ms.openlocfilehash: 7ac067e84f2a4d2724e3d8f2d0af9b220fd15538
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399659"
---
# \<serviceDiscovery>
Určuje zjistitelnost koncových bodů služby.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceDiscovery>**  
  
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
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<announcementEndpoint>](announcementendpoint.md)|Kolekce koncových bodů oznámení V této části můžete zadat koncové body, které se mají použít pro posílání zpráv s oznámením.|  
|[\<discoveryEndpoint>](discoveryendpoint.md)|Kolekce koncových bodů zjišťování. V této části můžete zadat koncové body, na kterých se mají zprávy zjišťování naslouchat.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|Určuje chování element.|  
  
## <a name="remarks"></a>Poznámky  
 Po přidání do konfigurace chování služby tento prvek konfigurace zpřístupňuje všechny koncové body této služby. Funkce zjišťování těchto koncových bodů můžete dále konfigurovat pomocí [\<discoveryEndpoint>](discoveryendpoint.md) [\<announcementEndpoint>](announcementendpoint.md) podřízených elementů nebo. Pomocí [\<announcementEndpoint>](announcementendpoint.md) části můžete nakonfigurovat oznámení zadáním konfigurace koncového bodu, která se bude používat k odesílání oznámení služby (online/Hello a offline/bye). Pomocí [\<discoveryEndpoint>](discoveryendpoint.md) oddílu můžete ručně zadat koncový bod, na kterém se mají zprávy zjišťování naslouchat.  
  
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
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>
