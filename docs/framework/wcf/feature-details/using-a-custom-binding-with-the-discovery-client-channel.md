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
# <a name="using-a-custom-binding-with-the-discovery-client-channel"></a><span data-ttu-id="eeb97-102">Použití vlastní vazby s kanálem klienta zjišťování</span><span class="sxs-lookup"><span data-stu-id="eeb97-102">Using a Custom Binding with the Discovery Client Channel</span></span>
<span data-ttu-id="eeb97-103">Při použití vlastní vazby s rozhraním je <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> nutné definovat a <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> vytvořit <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instance.</span><span class="sxs-lookup"><span data-stu-id="eeb97-103">When using a custom binding with the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, you must define a <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> that creates <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instances.</span></span>  
  
## <a name="creating-a-discoveryendpointprovider"></a><span data-ttu-id="eeb97-104">Vytvoření DiscoveryEndpointProvider</span><span class="sxs-lookup"><span data-stu-id="eeb97-104">Creating a DiscoveryEndpointProvider</span></span>  
 <span data-ttu-id="eeb97-105"><xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider>Zodpovídá za vytváření <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instancí na vyžádání.</span><span class="sxs-lookup"><span data-stu-id="eeb97-105">The <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> is responsible for creating <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instances on demand.</span></span> <span data-ttu-id="eeb97-106">Chcete-li definovat poskytovatele koncového bodu zjišťování, odvodit třídu z <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> a přepsat <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider.GetDiscoveryEndpoint%2A> metodu a vrátit nový koncový bod zjišťování.</span><span class="sxs-lookup"><span data-stu-id="eeb97-106">To define a discovery endpoint provider, derive a class from <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> and override the <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider.GetDiscoveryEndpoint%2A> method and return a new discovery endpoint.</span></span> <span data-ttu-id="eeb97-107">Následující příklad ukazuje, jak vytvořit poskytovatele koncového bodu zjišťování.</span><span class="sxs-lookup"><span data-stu-id="eeb97-107">The following example shows how to create a discovery endpoint provider.</span></span>  
  
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
  
 <span data-ttu-id="eeb97-108">Po definování poskytovatele koncového bodu zjišťování můžete vytvořit vlastní vazbu a přidat <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> , která odkazuje na poskytovatele koncového bodu zjišťování, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="eeb97-108">Once you have defined the discovery endpoint provider you can create a custom binding and add the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, which references the discovery endpoint provider as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="eeb97-109">Další informace o použití kanálu klienta zjišťování najdete v tématu [použití kanálu klienta zjišťování](using-the-discovery-client-channel.md).</span><span class="sxs-lookup"><span data-stu-id="eeb97-109">For more information about using the discovery client channel, see [Using the Discovery Client Channel](using-the-discovery-client-channel.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="eeb97-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="eeb97-110">See also</span></span>

- [<span data-ttu-id="eeb97-111">Přehled zjišťování WCF</span><span class="sxs-lookup"><span data-stu-id="eeb97-111">WCF Discovery Overview</span></span>](wcf-discovery-overview.md)
- [<span data-ttu-id="eeb97-112">Použití kanálu klienta zjišťování</span><span class="sxs-lookup"><span data-stu-id="eeb97-112">Using the Discovery Client Channel</span></span>](using-the-discovery-client-channel.md)
