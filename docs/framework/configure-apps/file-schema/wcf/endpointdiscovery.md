---
title: <endpointDiscovery>
ms.date: 03/30/2017
ms.assetid: 70812717-888a-4748-9640-0df6715ff029
ms.openlocfilehash: 5cb64c54067ba695f67d86c0026db77ebbe7d5ee
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919052"
---
# <a name="endpointdiscovery"></a>\<endpointDiscovery>
Určuje různá nastavení zjišťování pro koncový bod, například jeho zjistitelnost, obory a jakákoli vlastní rozšíření pro jeho metadata.  
  
\<system.ServiceModel>  
\<> chování  
\<endpointBehaviors>  
\<> chování  
\<endpointDiscovery>  
  
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
|enabled|Logická hodnota, která určuje, zda je na tomto koncovém bodu povolena zjistitelnost. Výchozí hodnota je `false`.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<> oborů](scopes.md)|Kolekce identifikátorů URI oboru pro koncový bod. K jednomu koncovému bodu lze přidružit více než jeden identifikátor URI oboru.|  
|rozšíření > [z \<> endpointDiscovery] [ \<](extensions.md)|Kolekce elementů XML, které umožňují zadat vlastní metadata, která budou publikována pro koncový bod.|  
|\<> typů|Kolekce rozhraní, která se mají vyhledat|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<> chování](behavior-of-endpointbehaviors.md)|Určuje chování element.|  
|||  
  
## <a name="remarks"></a>Poznámky  
 Po přidání do konfigurace chování koncového bodu a s `enabled` atributem nastaveným na `true`může tento prvek konfigurace povolit svou zjistitelnost. Kromě toho můžete použít [ \<rozsahy >](scopes.md)podřízených element k určení identifikátorů URI vlastního rozsahu, které lze použít k filtrování koncových bodů služby během dotazu a také [ \<rozšíření >](extensions.md) podřízený element k určení vlastního metadata, která se mají publikovat společně se standardními zjistitelnými metadaty (EPR, ContractTypeName, Binding, Scope a ListenURI).  
  
 Tento prvek konfigurace je závislý na [ \<prvku serviceDiscovery >](servicediscovery.md) , který poskytuje kontrolu úrovně služeb pro zjistitelnost. To znamená, že nastavení tohoto prvku budou ignorována, pokud [ \<serviceDiscovery >](servicediscovery.md) není v konfiguraci k dispozici.  
  
## <a name="example"></a>Příklad  
 Následující příklad konfigurace určuje rozsahy filtrování a metadata rozšíření, která se mají publikovat pro koncový bod.  
  
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
          <add scope="http://contoso/test1" />
          <add scope="http://contoso/test2" />
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
