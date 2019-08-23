---
title: <endpointExtensions>
ms.date: 03/30/2017
ms.assetid: 33396e0a-1fae-4616-b822-923584eebfd1
ms.openlocfilehash: fe57cb84cfa70b1f6b92abf1dbac89ddad9d4dc8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925699"
---
# <a name="endpointextensions"></a>\<endpointExtensions >
Tento oddíl registruje nový standardní koncový bod v oddílu rozšíření v počítači nebo v konfiguračním souboru aplikace. Standardní koncový bod můžete do této kolekce přidat pomocí `add` klíčového slova a `type` nastavením atributu prvku na typ koncového bodu a také `name` atributem na název standardního koncového bodu.  
  
 Následující příklad používá `add` prvek a také `name` atribut pro přidání standardního koncového bodu do `<endpointExtensions>` oddílu konfiguračního souboru.  
  
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
  
 Po registraci standardního koncového bodu ho můžete použít, jak je znázorněno v následujícím příkladu. V elementu`kind` `<endpointExtensions>` [ >koncovéhoboduurčujeatributstandardnítypkoncovéhobodu,kterýbyl\<](endpoint-element.md) zaregistrován v oddílu. Atribut bude totožný `name` s atributem konfiguračního prvku standardního koncového bodu v `<standardEndpoints>` oddílu. `endpointConfiguration`  
  
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
