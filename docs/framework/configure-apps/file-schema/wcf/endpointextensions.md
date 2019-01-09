---
title: '&lt;endpointExtensions&gt;'
ms.date: 03/30/2017
ms.assetid: 33396e0a-1fae-4616-b822-923584eebfd1
ms.openlocfilehash: 3883a23c679abc83d7cfe9011b7cdb7e4154adfe
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54146443"
---
# <a name="ltendpointextensionsgt"></a><span data-ttu-id="739f0-102">&lt;endpointExtensions&gt;</span><span class="sxs-lookup"><span data-stu-id="739f0-102">&lt;endpointExtensions&gt;</span></span>
<span data-ttu-id="739f0-103">Tento oddíl registruje nový standardní koncový bod v oddílu rozšíření, na počítači nebo konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="739f0-103">This section registers a new standard endpoint in the extensions section in a machine or application configuration file.</span></span> <span data-ttu-id="739f0-104">Standardní koncový bod můžete přidat do této kolekce pomocí `add` – klíčové slovo a nastavení `type` atribut elementu na koncový bod typu, stejně jako `name` atribut název standardního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="739f0-104">You can add a standard endpoint to this collection by using the `add` keyword, and setting the `type` attribute of the element to the endpoint type, as well as the `name` attribute to the name of the standard endpoint.</span></span>  
  
 <span data-ttu-id="739f0-105">Následující příklad používá `add` element, stejně jako `name` atribut pro standardní koncový bod pro přidání `<endpointExtensions>` oddílu konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="739f0-105">The following example uses the `add` element, as well as the `name` attribute to add a standard endpoint to the `<endpointExtensions>` section of the configuration file.</span></span>  
  
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
  
 <span data-ttu-id="739f0-106">Po registraci standardní koncový bod, můžete ji jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="739f0-106">After the standard endpoint has been registered, you can use it as shown in the following example.</span></span> <span data-ttu-id="739f0-107">V [ \<koncový bod >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) elementu, `kind` atribut určuje typ standardní koncový bod, který byl zaregistrován v `<endpointExtensions>` oddílu.</span><span class="sxs-lookup"><span data-stu-id="739f0-107">In the [\<endpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) element, the `kind` attribute specifies the standard endpoint type that has been registered in the `<endpointExtensions>` section.</span></span> <span data-ttu-id="739f0-108">`endpointConfiguration` Bude stejný jako atribut `name` atribut standardní koncový bod v elementu konfigurace `<standardEndpoints>` části.</span><span class="sxs-lookup"><span data-stu-id="739f0-108">The `endpointConfiguration` attribute will be identical to the `name` attribute of the configuration element of the standard endpoint in the `<standardEndpoints>` section.</span></span>  
  
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
  
