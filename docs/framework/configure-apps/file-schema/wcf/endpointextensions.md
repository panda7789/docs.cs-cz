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
