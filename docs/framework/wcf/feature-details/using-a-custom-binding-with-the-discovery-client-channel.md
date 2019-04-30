---
title: Použití vlastní vazby s kanálem klienta zjišťování
ms.date: 03/30/2017
ms.assetid: 36f95e75-04f7-44f3-a995-a0d623624d7f
ms.openlocfilehash: 6fe9370bb22ca424774fc8cb4566e0802bc06697
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61918616"
---
# <a name="using-a-custom-binding-with-the-discovery-client-channel"></a>Použití vlastní vazby s kanálem klienta zjišťování
Při použití vlastní vazby s <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, je nutné definovat <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> , který vytváří <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instancí.  
  
## <a name="creating-a-discoveryendpointprovider"></a>Vytváření DiscoveryEndpointProvider  
 <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> Zodpovídá za vytvoření <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instancí na vyžádání. K definování poskytovatele koncového bodu zjišťování, odvoďte třídu z <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> a přepsat <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider.GetDiscoveryEndpoint%2A> metodu a vrátí nový koncový bod zjišťování. Následující příklad ukazuje, jak vytvořit poskytovatele koncového bodu zjišťování.  
  
```  
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
  
 Po definování poskytovatele koncového bodu zjišťování můžete vytvořit vlastní vazby a přidat <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, který odkazuje na poskytovateli koncový bod zjišťování, jak je znázorněno v následujícím příkladu.  
  
```  
DiscoveryClientBindingElement discoveryBindingElement = new DiscoveryClientBindingElement();  
  
// Provide the search criteria and the endpoint over which the probe is sent.  
discoveryBindingElement.FindCriteria = new FindCriteria(typeof(ICalculatorService));  
discoveryBindingElement.DiscoveryEndpointProvider = new UdpDiscoveryEndpointProvider();  
  
CustomBinding customBinding = new CustomBinding(new NetTcpBinding());  
// Insert DiscoveryClientBindingElement at the top of the BindingElement stack.  
// An exception is thrown if this binding element is not at the top.  
customBinding.Elements.Insert(0, discoveryBindingElement);  
```  
  
 Další informace o použití kanálu klienta zjišťování najdete v tématu [použití kanálu klienta zjišťování](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md). 
  
## <a name="see-also"></a>Viz také:

- [Přehled zjišťování WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)
- [Použití kanálu klienta zjišťování](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md)
