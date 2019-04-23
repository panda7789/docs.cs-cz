---
title: 'Postupy: Určení verze zjišťování zkušebního požadavku'
ms.date: 03/30/2017
ms.assetid: b3c4e2e2-2957-4074-ae6a-776a5ca84278
ms.openlocfilehash: 6bd112be311eb9397ad89801be5358d67c7499fd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59332271"
---
# <a name="how-todetermine-the-discovery-version-of-a-probe-request"></a><span data-ttu-id="6e113-102">Postupy: Určení verze zjišťování zkušebního požadavku</span><span class="sxs-lookup"><span data-stu-id="6e113-102">How to:Determine the Discovery Version of a Probe Request</span></span>
<span data-ttu-id="6e113-103">Proxy zjišťování může vystavit několik koncových bodů zjišťování pomocí zjišťování různých verzí.</span><span class="sxs-lookup"><span data-stu-id="6e113-103">A discovery proxy may expose multiple discovery endpoints using different discovery versions.</span></span> <span data-ttu-id="6e113-104">Když vícesměrového vysílání UDP dorazí požadavek testu na proxy serveru proxy server by měl odpovědět vícesměrovou zprávu.</span><span class="sxs-lookup"><span data-stu-id="6e113-104">When a UDP multicast Probe request arrives at the proxy the proxy should respond with a multicast suppression message.</span></span> <span data-ttu-id="6e113-105">Pokud to chcete udělat byste museli znát verze zjišťování požadavku.</span><span class="sxs-lookup"><span data-stu-id="6e113-105">In order to do this it would have to know the discovery version of the request.</span></span>  
  
### <a name="to-determine-the-discovery-version-of-a-probe-request"></a><span data-ttu-id="6e113-106">K určení verze zjišťování zkušebního požadavku</span><span class="sxs-lookup"><span data-stu-id="6e113-106">To Determine the Discovery Version of a Probe Request</span></span>  
  
1. <span data-ttu-id="6e113-107">V metodě, která bude reagovat na požadavek testu (například <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A>) pomocí statické <xref:System.ServiceModel.OperationContext.Current%2A> vlastnost k vyhledání <xref:System.ServiceModel.Discovery.DiscoveryOperationContextExtension> jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="6e113-107">In the method that responds to a Probe request (for example <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A>) use the static <xref:System.ServiceModel.OperationContext.Current%2A> property to search for a <xref:System.ServiceModel.Discovery.DiscoveryOperationContextExtension> as shown in the following code.</span></span>  
  
    ```  
    DiscoveryOperationContextExtension doce = OperationContext.Current.Extensions.Find<DiscoveryOperationContextExtension>();  
    // Access the discovery version from the DiscoveryOperationContextExtension  
    doce.DiscoveryVersion;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="6e113-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6e113-108">See also</span></span>

- <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion%2A>
- [<span data-ttu-id="6e113-109">Implementace proxy zjišťování</span><span class="sxs-lookup"><span data-stu-id="6e113-109">Implementing a Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md)
