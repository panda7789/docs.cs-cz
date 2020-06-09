---
title: Použití vlastní vazby s kanálem klienta zjišťování
ms.date: 03/30/2017
ms.assetid: 36f95e75-04f7-44f3-a995-a0d623624d7f
ms.openlocfilehash: 49983c3ab303d3839350af72b1aa4821c071fe99
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595034"
---
# <a name="using-a-custom-binding-with-the-discovery-client-channel"></a>Použití vlastní vazby s kanálem klienta zjišťování
Při použití vlastní vazby s rozhraním je <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> nutné definovat a <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> vytvořit <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instance.  
  
## <a name="creating-a-discoveryendpointprovider"></a>Vytvoření DiscoveryEndpointProvider  
 <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider>Zodpovídá za vytváření <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instancí na vyžádání. Chcete-li definovat poskytovatele koncového bodu zjišťování, odvodit třídu z <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> a přepsat <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider.GetDiscoveryEndpoint%2A> metodu a vrátit nový koncový bod zjišťování. Následující příklad ukazuje, jak vytvořit poskytovatele koncového bodu zjišťování.  
  
```csharp
// Extend DiscoveryEndpointProvider class to change the default DiscoveryEndpoint  
// to the DiscoveryClientBindingElement. The Discovery ClientChannel
// uses this endpoint to send Probe message.  
public class UdpDiscoveryEndpointProvider : DiscoveryEndpointProvider  
{  
   public override DiscoveryEndpoint GetDiscoveryEndpoint()  
   {  
      return new UdpDiscoveryEndpoint(DiscoveryVersion.WSDiscoveryApril2005);  
   }  
}  
```  
  
 Po definování poskytovatele koncového bodu zjišťování můžete vytvořit vlastní vazbu a přidat <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> , která odkazuje na poskytovatele koncového bodu zjišťování, jak je znázorněno v následujícím příkladu.  
  
```csharp
DiscoveryClientBindingElement discoveryBindingElement = new DiscoveryClientBindingElement();  
  
// Provide the search criteria and the endpoint over which the probe is sent.  
discoveryBindingElement.FindCriteria = new FindCriteria(typeof(ICalculatorService));  
discoveryBindingElement.DiscoveryEndpointProvider = new UdpDiscoveryEndpointProvider();  
  
CustomBinding customBinding = new CustomBinding(new NetTcpBinding());  
// Insert DiscoveryClientBindingElement at the top of the BindingElement stack.  
// An exception is thrown if this binding element is not at the top.  
customBinding.Elements.Insert(0, discoveryBindingElement);  
```  
  
 Další informace o použití kanálu klienta zjišťování najdete v tématu [použití kanálu klienta zjišťování](using-the-discovery-client-channel.md).
  
## <a name="see-also"></a>Viz také

- [Přehled zjišťování WCF](wcf-discovery-overview.md)
- [Použití kanálu klienta zjišťování](using-the-discovery-client-channel.md)
