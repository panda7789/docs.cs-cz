---
title: '&lt;serviceDiscovery&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a3c68a4a-fc95-43c5-aacb-785936c0cf39
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9bdd16e02742baa14d1ebd11ea95591df7093705
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltservicediscoverygt"></a>&lt;serviceDiscovery&gt;
Určuje možnosti rozpoznání koncových bodů služby.  
  
 \<systém. ServiceModel >  
\<chování >  
\<serviceBehaviors >  
\<chování >  
\<serviceDiscovery >  
  
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
|[\<announcementEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md)|Kolekce koncových bodů oznámení. Pomocí této části můžete určovat koncové body k použití pro odesílání zpráv oznámení.|  
|[\<discoveryEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md)|Kolekce zjišťování koncových bodů. V této části použijte k určení koncových bodů, na kterém se má naslouchat pro zprávy zjišťování.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<chování >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Určuje chování element.|  
  
## <a name="remarks"></a>Poznámky  
 Když se přidá do konfigurace chování služby, tento element konfigurace zajistí koncové body služeb zjistitelný. Funkce zjišťování těchto koncových bodů lze dále konfigurovat pomocí [ \<discoveryEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md) nebo [ \<announcementEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md) podřízené elementy. Použít [ \<announcementEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md) část konfigurace hlášení zadáním konfigurace koncového bodu, která se má použít k odeslání oznámení týkající se služeb (nebo Hello je online a offline nebo Bye). Použití [ \<discoveryEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md) části ručně zadat koncový bod, ke kterému chcete přijímat zprávy zjišťování.  
  
## <a name="example"></a>Příklad  
 Následující příklad konfigurace určuje, že CalculatorService zjistitelné a volitelně specifikuje koncového bodu oznámení má být použit.  
  
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
 <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>
