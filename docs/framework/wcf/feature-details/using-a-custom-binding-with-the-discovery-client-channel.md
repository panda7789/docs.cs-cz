---
title: "Použití vlastní vazby s kanálem klienta zjišťování"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 36f95e75-04f7-44f3-a995-a0d623624d7f
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c18be6868c2b0d092d1924b227b444b8b679a383
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="using-a-custom-binding-with-the-discovery-client-channel"></a>Použití vlastní vazby s kanálem klienta zjišťování
Při použití vlastní vazby s <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, je nutné definovat <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> vytvářející <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instance.  
  
## <a name="creating-a-discoveryendpointprovider"></a>Vytváření DiscoveryEndpointProvider  
 <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> Zodpovídá za vytvoření <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instance na vyžádání. K definování zjišťování zprostředkovatele koncových bodů, odvození třídy z <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> a přepsat <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider.GetDiscoveryEndpoint%2A> metoda a vraťte se nový koncový bod zjišťování. Následující příklad ukazuje, jak vytvořit poskytovatele koncový bod zjišťování.  
  
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
  
 Jakmile definujete zprostředkovatele zjišťování koncových bodů, které můžete vytvořit vlastní vazby a přidat <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, který odkazuje na zprostředkovatele zjišťování koncových bodů, jak je znázorněno v následujícím příkladu.  
  
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
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]pomocí kanálem klienta zjišťování, najdete v tématu [pomocí kanálem klienta zjišťování](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md). Úplný příklad, naleznete v tématu [– ukázka prvky vazby zjišťování](../../../../docs/framework/wcf/samples/discovery-binding-element-sample.md)  
  
## <a name="see-also"></a>Viz také  
 [Přehled zjišťování WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
 [Pomocí kanálem klienta zjišťování](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md)  
 [Zjišťování – ukázka prvky vazby](../../../../docs/framework/wcf/samples/discovery-binding-element-sample.md)
