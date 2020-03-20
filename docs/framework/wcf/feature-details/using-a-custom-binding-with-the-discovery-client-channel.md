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
# <a name="using-a-custom-binding-with-the-discovery-client-channel"></a><span data-ttu-id="803be-102">Použití vlastní vazby s kanálem klienta zjišťování</span><span class="sxs-lookup"><span data-stu-id="803be-102">Using a Custom Binding with the Discovery Client Channel</span></span>
<span data-ttu-id="803be-103">Při použití vlastní vazby s <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> musíte <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> definovat, který vytváří instance.</span><span class="sxs-lookup"><span data-stu-id="803be-103">When using a custom binding with the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, you must define a <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> that creates <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instances.</span></span>  
  
## <a name="creating-a-discoveryendpointprovider"></a><span data-ttu-id="803be-104">Vytvoření zjišťování Zjišťování EndpointProvider</span><span class="sxs-lookup"><span data-stu-id="803be-104">Creating a DiscoveryEndpointProvider</span></span>  
 <span data-ttu-id="803be-105">Je <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> zodpovědný za <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> vytváření instancí na vyžádání.</span><span class="sxs-lookup"><span data-stu-id="803be-105">The <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> is responsible for creating <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instances on demand.</span></span> <span data-ttu-id="803be-106">Chcete-li definovat zprostředkovatele koncového <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> bodu zjišťování, <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider.GetDiscoveryEndpoint%2A> odvodit třídu z metody a přepsat metodu a vrátit nový koncový bod zjišťování.</span><span class="sxs-lookup"><span data-stu-id="803be-106">To define a discovery endpoint provider, derive a class from <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> and override the <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider.GetDiscoveryEndpoint%2A> method and return a new discovery endpoint.</span></span> <span data-ttu-id="803be-107">Následující příklad ukazuje, jak vytvořit zprostředkovatele koncového bodu zjišťování.</span><span class="sxs-lookup"><span data-stu-id="803be-107">The following example shows how to create a discovery endpoint provider.</span></span>  
  
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
  
 <span data-ttu-id="803be-108">Po definování zprostředkovatele koncového bodu zjišťování můžete vytvořit <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>vlastní vazbu a přidat , který odkazuje na zprostředkovatele koncového bodu zjišťování, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="803be-108">Once you have defined the discovery endpoint provider you can create a custom binding and add the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, which references the discovery endpoint provider as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="803be-109">Další informace o použití kanálu klienta zjišťování naleznete [v tématu Použití kanálu klienta zjišťování](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md).</span><span class="sxs-lookup"><span data-stu-id="803be-109">For more information about using the discovery client channel, see [Using the Discovery Client Channel](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="803be-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="803be-110">See also</span></span>

- [<span data-ttu-id="803be-111">Přehled zjišťování WCF</span><span class="sxs-lookup"><span data-stu-id="803be-111">WCF Discovery Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)
- [<span data-ttu-id="803be-112">Použití kanálu klienta zjišťování</span><span class="sxs-lookup"><span data-stu-id="803be-112">Using the Discovery Client Channel</span></span>](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md)
