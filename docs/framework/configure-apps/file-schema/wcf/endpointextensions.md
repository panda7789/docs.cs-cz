---
title: '&lt;endpointExtensions&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 33396e0a-1fae-4616-b822-923584eebfd1
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 47aad13591e3a35433cafea3e49fff7fa6e7b7c2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltendpointextensionsgt"></a>&lt;endpointExtensions&gt;
Tato část zaregistruje nový standardní koncový bod v části rozšíření na počítači nebo konfiguračního souboru aplikace. Koncový bod standardní můžete přidat do této kolekce pomocí `add` – klíčové slovo a nastavení `type` atribut elementu typ koncového bodu, a taky `name` atribut název standardní koncového bodu.  
  
 Následující příklad používá `add` element společně s `name` k přidání standardní koncového bodu do atribut `<endpointExtensions>` oddílu konfiguračního souboru.  
  
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
  
 Po registraci standardní koncový bod, můžete použít jak je znázorněno v následujícím příkladu. V [ \<endpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) elementu, `kind` atribut určuje typ standardní koncového bodu, který byl zaregistrován v `<endpointExtensions>` oddílu. `endpointConfiguration` Atribut budou stejné `name` atribut elementu konfigurace standardní koncového bodu v `<standardEndpoints>` oddílu.  
  
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
        <standardEndpoint  
                  name="udpConfig"  
                  multicastAddress="soap.udp://239.255.255.250:3703"  
                  ... />  
      </udpDiscoveryEndpoint>  
    </standardEndpoints>  
  </system.serviceModel>  
```
