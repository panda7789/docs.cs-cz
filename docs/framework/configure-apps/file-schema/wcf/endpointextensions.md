---
title: <endpointExtensions>
ms.date: 03/30/2017
ms.assetid: 33396e0a-1fae-4616-b822-923584eebfd1
ms.openlocfilehash: 746f98b54285f95bb63e15136508909327c0d140
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55264606"
---
# <a name="endpointextensions"></a>\<endpointExtensions>
Tento oddíl registruje nový standardní koncový bod v oddílu rozšíření, na počítači nebo konfiguračního souboru aplikace. Standardní koncový bod můžete přidat do této kolekce pomocí `add` – klíčové slovo a nastavení `type` atribut elementu na koncový bod typu, stejně jako `name` atribut název standardního koncového bodu.  
  
 Následující příklad používá `add` element, stejně jako `name` atribut pro standardní koncový bod pro přidání `<endpointExtensions>` oddílu konfiguračního souboru.  
  
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
  
 Po registraci standardní koncový bod, můžete ji jak je znázorněno v následujícím příkladu. V [ \<koncový bod >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) elementu, `kind` atribut určuje typ standardní koncový bod, který byl zaregistrován v `<endpointExtensions>` oddílu. `endpointConfiguration` Bude stejný jako atribut `name` atribut standardní koncový bod v elementu konfigurace `<standardEndpoints>` části.  
  
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
  
