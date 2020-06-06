---
title: <endpointExtensions>
ms.date: 03/30/2017
ms.assetid: 33396e0a-1fae-4616-b822-923584eebfd1
ms.openlocfilehash: fe57cb84cfa70b1f6b92abf1dbac89ddad9d4dc8
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "69925699"
---
# \<endpointExtensions>
<span data-ttu-id="7f3f8-101">Tento oddíl registruje nový standardní koncový bod v oddílu rozšíření v počítači nebo v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="7f3f8-101">This section registers a new standard endpoint in the extensions section in a machine or application configuration file.</span></span> <span data-ttu-id="7f3f8-102">Standardní koncový bod můžete do této kolekce přidat pomocí `add` klíčového slova a nastavením `type` atributu prvku na typ koncového bodu a také `name` atributem na název standardního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="7f3f8-102">You can add a standard endpoint to this collection by using the `add` keyword, and setting the `type` attribute of the element to the endpoint type, as well as the `name` attribute to the name of the standard endpoint.</span></span>  
  
 <span data-ttu-id="7f3f8-103">Následující příklad používá `add` prvek a také `name` atribut pro přidání standardního koncového bodu do `<endpointExtensions>` oddílu konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="7f3f8-103">The following example uses the `add` element, as well as the `name` attribute to add a standard endpoint to the `<endpointExtensions>` section of the configuration file.</span></span>  
  
```xml  
<system.serviceModel>
  <extensions>
    <endpointExtensions>
      <add name="udpDiscoveryEndpoint"
           type="System.Discovery.UdpEndpointCollectionElement, System.Discovery.dll, Version=1.0.0.0, Culture=neutral, PublicKeyToken=ffffffffffffffff"/>
    </endpointExtensions>
  </extensions>
</system.serviceModel>
```  
  
 <span data-ttu-id="7f3f8-104">Po registraci standardního koncového bodu ho můžete použít, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="7f3f8-104">After the standard endpoint has been registered, you can use it as shown in the following example.</span></span> <span data-ttu-id="7f3f8-105">V [\<endpoint>](endpoint-element.md) elementu `kind` určuje atribut standardní typ koncového bodu, který je zaregistrován v `<endpointExtensions>` části.</span><span class="sxs-lookup"><span data-stu-id="7f3f8-105">In the [\<endpoint>](endpoint-element.md) element, the `kind` attribute specifies the standard endpoint type that has been registered in the `<endpointExtensions>` section.</span></span> <span data-ttu-id="7f3f8-106">`endpointConfiguration`Atribut bude totožný s `name` atributem konfiguračního prvku standardního koncového bodu v `<standardEndpoints>` oddílu.</span><span class="sxs-lookup"><span data-stu-id="7f3f8-106">The `endpointConfiguration` attribute will be identical to the `name` attribute of the configuration element of the standard endpoint in the `<standardEndpoints>` section.</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service name="Service1">
      <endpoint kind="udpDiscoveryEndpoint"
                endpointConfiguration="udpConfig" />
    </service>
  </services>
  <standardEndpoints>
    <udpDiscoveryEndpoint>
      <standardEndpoint name="udpConfig"
                        multicastAddress="soap.udp://239.255.255.250:3703"
                        ... />
    </udpDiscoveryEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
