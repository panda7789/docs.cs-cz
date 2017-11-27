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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3c0d9dd167dbef4a641566e3d89abcdaf7c0302a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="ltendpointextensionsgt"></a><span data-ttu-id="3c631-102">&lt;endpointExtensions&gt;</span><span class="sxs-lookup"><span data-stu-id="3c631-102">&lt;endpointExtensions&gt;</span></span>
<span data-ttu-id="3c631-103">Tato část zaregistruje nový standardní koncový bod v části rozšíření na počítači nebo konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="3c631-103">This section registers a new standard endpoint in the extensions section in a machine or application configuration file.</span></span> <span data-ttu-id="3c631-104">Koncový bod standardní můžete přidat do této kolekce pomocí `add` – klíčové slovo a nastavení `type` atribut elementu typ koncového bodu, a taky `name` atribut název standardní koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="3c631-104">You can add a standard endpoint to this collection by using the `add` keyword, and setting the `type` attribute of the element to the endpoint type, as well as the `name` attribute to the name of the standard endpoint.</span></span>  
  
 <span data-ttu-id="3c631-105">Následující příklad používá `add` element společně s `name` k přidání standardní koncového bodu do atribut `<endpointExtensions>` oddílu konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="3c631-105">The following example uses the `add` element, as well as the `name` attribute to add a standard endpoint to the `<endpointExtensions>` section of the configuration file.</span></span>  
  
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
  
 <span data-ttu-id="3c631-106">Po registraci standardní koncový bod, můžete použít jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="3c631-106">After the standard endpoint has been registered, you can use it as shown in the following example.</span></span> <span data-ttu-id="3c631-107">V [ \<endpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) elementu, `kind` atribut určuje typ standardní koncového bodu, který byl zaregistrován v `<endpointExtensions>` oddílu.</span><span class="sxs-lookup"><span data-stu-id="3c631-107">In the [\<endpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) element, the `kind` attribute specifies the standard endpoint type that has been registered in the `<endpointExtensions>` section.</span></span> <span data-ttu-id="3c631-108">`endpointConfiguration` Atribut budou stejné `name` atribut elementu konfigurace standardní koncového bodu v `<standardEndpoints>` oddílu.</span><span class="sxs-lookup"><span data-stu-id="3c631-108">The `endpointConfiguration` attribute will be identical to the `name` attribute of the configuration element of the standard endpoint in the `<standardEndpoints>` section.</span></span>  
  
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
