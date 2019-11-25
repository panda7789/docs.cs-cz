---
title: Použití vlastní vazby s kanálem klienta zjišťování
ms.date: 03/30/2017
ms.assetid: 36f95e75-04f7-44f3-a995-a0d623624d7f
ms.openlocfilehash: 406a53dece6370fbb56daa5a30b52621ca1dcd6d
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975982"
---
# <a name="using-a-custom-binding-with-the-discovery-client-channel"></a><span data-ttu-id="5e097-102">Použití vlastní vazby s kanálem klienta zjišťování</span><span class="sxs-lookup"><span data-stu-id="5e097-102">Using a Custom Binding with the Discovery Client Channel</span></span>
<span data-ttu-id="5e097-103">Při použití vlastní vazby s <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>je nutné definovat <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider>, který vytváří instance <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="5e097-103">When using a custom binding with the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, you must define a <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> that creates <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instances.</span></span>  
  
## <a name="creating-a-discoveryendpointprovider"></a><span data-ttu-id="5e097-104">Vytvoření DiscoveryEndpointProvider</span><span class="sxs-lookup"><span data-stu-id="5e097-104">Creating a DiscoveryEndpointProvider</span></span>  
 <span data-ttu-id="5e097-105"><xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> zodpovídá za vytváření instancí <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> na vyžádání.</span><span class="sxs-lookup"><span data-stu-id="5e097-105">The <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> is responsible for creating <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instances on demand.</span></span> <span data-ttu-id="5e097-106">Chcete-li definovat poskytovatele koncového bodu zjišťování, odvodit třídu z <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> a přepsat metodu <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider.GetDiscoveryEndpoint%2A> a vrátit nový koncový bod zjišťování.</span><span class="sxs-lookup"><span data-stu-id="5e097-106">To define a discovery endpoint provider, derive a class from <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> and override the <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider.GetDiscoveryEndpoint%2A> method and return a new discovery endpoint.</span></span> <span data-ttu-id="5e097-107">Následující příklad ukazuje, jak vytvořit poskytovatele koncového bodu zjišťování.</span><span class="sxs-lookup"><span data-stu-id="5e097-107">The following example shows how to create a discovery endpoint provider.</span></span>  
  
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
  
 <span data-ttu-id="5e097-108">Po definování poskytovatele koncového bodu zjišťování můžete vytvořit vlastní vazbu a přidat <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, která odkazuje na poskytovatele koncového bodu zjišťování, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="5e097-108">Once you have defined the discovery endpoint provider you can create a custom binding and add the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, which references the discovery endpoint provider as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="5e097-109">Další informace o použití kanálu klienta zjišťování najdete v tématu [použití kanálu klienta zjišťování](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md).</span><span class="sxs-lookup"><span data-stu-id="5e097-109">For more information about using the discovery client channel, see [Using the Discovery Client Channel](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md).</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="5e097-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5e097-110">See also</span></span>

- [<span data-ttu-id="5e097-111">Přehled zjišťování WCF</span><span class="sxs-lookup"><span data-stu-id="5e097-111">WCF Discovery Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)
- [<span data-ttu-id="5e097-112">Použití kanálu klienta zjišťování</span><span class="sxs-lookup"><span data-stu-id="5e097-112">Using the Discovery Client Channel</span></span>](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md)
