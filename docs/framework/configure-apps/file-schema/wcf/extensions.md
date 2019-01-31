---
title: <extensions>
ms.date: 03/30/2017
ms.assetid: bcfe5c44-04ef-4a20-96a5-90bfadf39623
ms.openlocfilehash: feac4999438a67043899eef98bb8b49644ee30d9
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55270014"
---
# <a name="extensions"></a><span data-ttu-id="385c7-101">\<Rozšíření ></span><span class="sxs-lookup"><span data-stu-id="385c7-101">\<extensions></span></span>
<span data-ttu-id="385c7-102">Tento prvek konfigurace obsahuje kolekci elementů XML, které obsahují vlastní metadata, aby byly publikované a společně s standardní zjistitelné metadata (EPR, ContractTypeName, BindingName, oboru a ListenURI).</span><span class="sxs-lookup"><span data-stu-id="385c7-102">This configuration element contains a collection of XML elements that contain custom metadata to be published along with the standard discoverable metadata (EPR, ContractTypeName, BindingName, Scope and ListenURI).</span></span> <span data-ttu-id="385c7-103">Následuje příklad použití tohoto konfiguračního prvku.</span><span class="sxs-lookup"><span data-stu-id="385c7-103">The following is an example of using this configuration element.</span></span>  
  
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
      <endpointDiscovery enable="true">
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
  
## <a name="see-also"></a><span data-ttu-id="385c7-104">Viz také:</span><span class="sxs-lookup"><span data-stu-id="385c7-104">See also</span></span>
- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
