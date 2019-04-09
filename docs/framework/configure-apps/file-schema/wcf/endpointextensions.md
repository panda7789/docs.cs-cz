---
title: <endpointExtensions>
ms.date: 03/30/2017
ms.assetid: 33396e0a-1fae-4616-b822-923584eebfd1
ms.openlocfilehash: 12ac8d9a7b0ed584fb1308e56d197a03b1c53e51
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59174925"
---
# <a name="endpointextensions"></a><span data-ttu-id="916c8-101">\<endpointExtensions></span><span class="sxs-lookup"><span data-stu-id="916c8-101">\<endpointExtensions></span></span>
<span data-ttu-id="916c8-102">Tento oddíl registruje nový standardní koncový bod v oddílu rozšíření, na počítači nebo konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="916c8-102">This section registers a new standard endpoint in the extensions section in a machine or application configuration file.</span></span> <span data-ttu-id="916c8-103">Standardní koncový bod můžete přidat do této kolekce pomocí `add` – klíčové slovo a nastavení `type` atribut elementu na koncový bod typu, stejně jako `name` atribut název standardního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="916c8-103">You can add a standard endpoint to this collection by using the `add` keyword, and setting the `type` attribute of the element to the endpoint type, as well as the `name` attribute to the name of the standard endpoint.</span></span>  
  
 <span data-ttu-id="916c8-104">Následující příklad používá `add` element, stejně jako `name` atribut pro standardní koncový bod pro přidání `<endpointExtensions>` oddílu konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="916c8-104">The following example uses the `add` element, as well as the `name` attribute to add a standard endpoint to the `<endpointExtensions>` section of the configuration file.</span></span>  
  
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
  
 <span data-ttu-id="916c8-105">Po registraci standardní koncový bod, můžete ji jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="916c8-105">After the standard endpoint has been registered, you can use it as shown in the following example.</span></span> <span data-ttu-id="916c8-106">V [ \<koncový bod >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) elementu, `kind` atribut určuje typ standardní koncový bod, který byl zaregistrován v `<endpointExtensions>` oddílu.</span><span class="sxs-lookup"><span data-stu-id="916c8-106">In the [\<endpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) element, the `kind` attribute specifies the standard endpoint type that has been registered in the `<endpointExtensions>` section.</span></span> <span data-ttu-id="916c8-107">`endpointConfiguration` Bude stejný jako atribut `name` atribut standardní koncový bod v elementu konfigurace `<standardEndpoints>` části.</span><span class="sxs-lookup"><span data-stu-id="916c8-107">The `endpointConfiguration` attribute will be identical to the `name` attribute of the configuration element of the standard endpoint in the `<standardEndpoints>` section.</span></span>  
  
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
