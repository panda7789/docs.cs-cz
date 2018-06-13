---
title: 'Postupy: Určení verze zjišťování zkušebního požadavku'
ms.date: 03/30/2017
ms.assetid: b3c4e2e2-2957-4074-ae6a-776a5ca84278
ms.openlocfilehash: 8ac9804b0fe46ca5fbe580d713ec82a2f9bb0128
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33489778"
---
# <a name="how-todetermine-the-discovery-version-of-a-probe-request"></a><span data-ttu-id="b4960-102">Postupy: Určení verze zjišťování zkušebního požadavku</span><span class="sxs-lookup"><span data-stu-id="b4960-102">How to:Determine the Discovery Version of a Probe Request</span></span>
<span data-ttu-id="b4960-103">Zjišťování proxy vystavuje několik koncových bodů zjišťování pomocí různých zjišťování verze.</span><span class="sxs-lookup"><span data-stu-id="b4960-103">A discovery proxy may expose multiple discovery endpoints using different discovery versions.</span></span> <span data-ttu-id="b4960-104">Když UDP, vícesměrového vysílání zkušebního požadavku dorazí na proxy server, které proxy server by měl odpovídat zprávy vícesměrového vysílání potlačení.</span><span class="sxs-lookup"><span data-stu-id="b4960-104">When a UDP multicast Probe request arrives at the proxy the proxy should respond with a multicast suppression message.</span></span> <span data-ttu-id="b4960-105">Pokud to chcete provést by mít vědět verze zjišťování požadavku.</span><span class="sxs-lookup"><span data-stu-id="b4960-105">In order to do this it would have to know the discovery version of the request.</span></span>  
  
### <a name="to-determine-the-discovery-version-of-a-probe-request"></a><span data-ttu-id="b4960-106">Určení verze zjišťování zkušebního požadavku</span><span class="sxs-lookup"><span data-stu-id="b4960-106">To Determine the Discovery Version of a Probe Request</span></span>  
  
1.  <span data-ttu-id="b4960-107">V metodě odpoví na žádost o test (třeba <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A>) použít statickou <xref:System.ServiceModel.OperationContext.Current%2A> vlastnost k vyhledání <xref:System.ServiceModel.Discovery.DiscoveryOperationContextExtension> jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="b4960-107">In the method that responds to a Probe request (for example <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A>) use the static <xref:System.ServiceModel.OperationContext.Current%2A> property to search for a <xref:System.ServiceModel.Discovery.DiscoveryOperationContextExtension> as shown in the following code.</span></span>  
  
    ```  
    DiscoveryOperationContextExtension doce = OperationContext.Current.Extensions.Find<DiscoveryOperationContextExtension>();  
    // Access the discovery version from the DiscoveryOperationContextExtension  
    doce.DiscoveryVersion;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="b4960-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="b4960-108">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion%2A>  
 [<span data-ttu-id="b4960-109">Implementace proxy zjišťování</span><span class="sxs-lookup"><span data-stu-id="b4960-109">Implementing a Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md)  
 [<span data-ttu-id="b4960-110">Ukázka proxy zjišťování</span><span class="sxs-lookup"><span data-stu-id="b4960-110">Discovery Proxy Sample</span></span>](../../../../docs/framework/wcf/samples/discovery-proxy-sample.md)
