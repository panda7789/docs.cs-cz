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
Tento oddíl registruje nový standardní koncový bod v oddílu rozšíření v počítači nebo v konfiguračním souboru aplikace. Standardní koncový bod můžete do této kolekce přidat pomocí `add` klíčového slova a nastavením `type` atributu prvku na typ koncového bodu a také `name` atributem na název standardního koncového bodu.  
  
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
  
 Po registraci standardního koncového bodu ho můžete použít, jak je znázorněno v následujícím příkladu. V [\<endpoint>](endpoint-element.md) elementu `kind` určuje atribut standardní typ koncového bodu, který je zaregistrován v `<endpointExtensions>` části. `endpointConfiguration`Atribut bude totožný s `name` atributem konfiguračního prvku standardního koncového bodu v `<standardEndpoints>` oddílu.  
  
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
