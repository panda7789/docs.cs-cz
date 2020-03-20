---
title: Použití vlastní vazby s kanálem klienta zjišťování
ms.date: 03/30/2017
ms.assetid: 36f95e75-04f7-44f3-a995-a0d623624d7f
ms.openlocfilehash: 5f3f5fe24d1f19ce503b793d9aad870d882c7971
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184292"
---
# <a name="using-a-custom-binding-with-the-discovery-client-channel"></a>Použití vlastní vazby s kanálem klienta zjišťování
Při použití vlastní vazby s <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> musíte <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> definovat, který vytváří instance.  
  
## <a name="creating-a-discoveryendpointprovider"></a>Vytvoření zjišťování Zjišťování EndpointProvider  
 Je <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> zodpovědný za <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> vytváření instancí na vyžádání. Chcete-li definovat zprostředkovatele koncového <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> bodu zjišťování, <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider.GetDiscoveryEndpoint%2A> odvodit třídu z metody a přepsat metodu a vrátit nový koncový bod zjišťování. Následující příklad ukazuje, jak vytvořit zprostředkovatele koncového bodu zjišťování.  
  
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
  
 Po definování zprostředkovatele koncového bodu zjišťování můžete vytvořit <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>vlastní vazbu a přidat , který odkazuje na zprostředkovatele koncového bodu zjišťování, jak je znázorněno v následujícím příkladu.  
  
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
  
 Další informace o použití kanálu klienta zjišťování naleznete [v tématu Použití kanálu klienta zjišťování](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md).
  
## <a name="see-also"></a>Viz také

- [Přehled zjišťování WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)
- [Použití kanálu klienta zjišťování](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md)
