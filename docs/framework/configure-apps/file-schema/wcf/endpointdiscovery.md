---
title: '&lt;endpointDiscovery&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 70812717-888a-4748-9640-0df6715ff029
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7a997ddffa2267cdeb9e54bb98d4122db254104d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltendpointdiscoverygt"></a>&lt;endpointDiscovery&gt;
Určuje různé zjišťování nastavení pro koncový bod, například jeho možnosti rozpoznání, obory a vlastní rozšíření jeho metadata.  
  
\<systém. ServiceModel >  
\<chování >  
\<endpointBehaviors >  
\<chování >  
\<endpointDiscovery >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="String">
      <endpointDiscovery enabled="Boolean">
        <scopes>
          <add scope="URI"/>
        </scopes>
        <extensions />
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|povoleno|Logická hodnota, který určuje, jestli je povolené možnosti rozpoznání na tento koncový bod. Výchozí hodnota je `false`.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<obory >](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|Kolekce oboru identifikátory URI pro koncový bod. Více než jednoho oboru identifikátory URI lze přidružit jeden koncový bod.|  
|[\<Rozšíření >](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) [z \<endpointDiscovery >]|Kolekce elementů XML, která umožňuje zadat vlastní metadata publikována pro koncový bod.|  
|\<typy >|Kolekce rozhraní pro vyhledávání.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<chování >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Určuje chování element.|  
|||  
  
## <a name="remarks"></a>Poznámky  
 Při přidání do konfigurace chování pro koncový bod a s `enabled` atribut nastaven na `true`, tento element konfigurace umožňuje jeho možnosti rozpoznání. Kromě toho můžete použít [ \<obory >](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)podřízený element pro zadání vlastní rozsah identifikátory URI, které mohou být použity k filtrování koncové body služby během dotazu, a taky [ \<rozšíření >](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) podřízený element k určení vlastních metadat, která by měla být publikována spolu s metadaty standardní zjistitelný (EPR, ContractTypeName, BindingName, oboru a adrese ListenURI).  
  
 Tento element konfigurace je závislá na [ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) element, který poskytuje možnosti rozpoznání úrovně řízení služby. To znamená, že tento element nastavení ignorují Pokud [ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) se nenachází v konfiguraci.  
  
## <a name="example"></a>Příklad  
 Následující příklad konfigurace určuje filtrování obory a rozšíření metadata publikována pro koncový bod.  
  
```xml  
<services>  
  <service name="CalculatorService"  
           behaviorConfiguration="CalculatorServiceBehavior">  
     <endpoint binding="basicHttpBinding"  
              address="calculator"  
              contract="ICalculatorService"  
              behaviorConfiguration="calculatorEndpointBehavior" />  
  </service>  
</services>  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <serviceDiscovery />  
    </behavior>  
  </serviceBehaviors>  
  <endpointBehaviors>  
    <behavior name="calculatorEndpointBehavior">  
      <endpointDiscovery enabled="true">  
        <scopes>  
          <add scope="http://contoso/test1"/>  
          <add scope="http://contoso/test2"/>  
        </scopes>  
        <extensions>  
          <e:Publisher xmlns:e="http://example.org">  
            <e:Name>The Example Organization</e:Name>  
            <e:Address>One Example Way, ExampleTown, EX 12345</e:Address>  
            <e:Contact>support@example.org</e:Contact>  
          </e:Publisher>  
          <AnotherCustomMetadata>Custom Metadata</AnotherCustomMetadata>  
        </extensions>  
      </endpointDiscovery>  
    </behavior>  
  </endpointBehaviors>  
</behaviors>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
