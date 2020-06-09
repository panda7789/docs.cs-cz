---
title: 'Postupy: Určení verze zjišťování zkušebního požadavku'
ms.date: 03/30/2017
ms.assetid: b3c4e2e2-2957-4074-ae6a-776a5ca84278
ms.openlocfilehash: 2b7e42714ae1d16a84bcb6f0fc79cf5b376a7a16
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595411"
---
# <a name="how-todetermine-the-discovery-version-of-a-probe-request"></a><span data-ttu-id="66727-102">Postupy: Určení verze zjišťování zkušebního požadavku</span><span class="sxs-lookup"><span data-stu-id="66727-102">How to:Determine the Discovery Version of a Probe Request</span></span>

<span data-ttu-id="66727-103">Proxy zjišťování může vystavit několik koncových bodů zjišťování pomocí různých verzí zjišťování.</span><span class="sxs-lookup"><span data-stu-id="66727-103">A discovery proxy may expose multiple discovery endpoints using different discovery versions.</span></span> <span data-ttu-id="66727-104">Když požadavek na test vícesměrového vysílání UDP dorazí na proxy server, měl by proxy reagovat se zprávou o potlačení vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="66727-104">When a UDP multicast Probe request arrives at the proxy, the proxy should respond with a multicast suppression message.</span></span> <span data-ttu-id="66727-105">Aby to bylo možné, museli byste znát verzi zjišťování žádosti.</span><span class="sxs-lookup"><span data-stu-id="66727-105">In order to do this, it would have to know the discovery version of the request.</span></span>

## <a name="to-determine-the-discovery-version-of-a-probe-request"></a><span data-ttu-id="66727-106">Určení verze zjišťování žádosti sondy</span><span class="sxs-lookup"><span data-stu-id="66727-106">To Determine the Discovery Version of a Probe Request</span></span>

<span data-ttu-id="66727-107">V metodě, která reaguje na požadavek sondy (například <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A?displayProperty=nameWithType> ), použijte statickou <xref:System.ServiceModel.OperationContext.Current%2A?displayProperty=nameWithType> vlastnost k vyhledání a <xref:System.ServiceModel.Discovery.DiscoveryOperationContextExtension> , jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="66727-107">In the method that responds to a Probe request (for example <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A?displayProperty=nameWithType>) use the static <xref:System.ServiceModel.OperationContext.Current%2A?displayProperty=nameWithType> property to search for a <xref:System.ServiceModel.Discovery.DiscoveryOperationContextExtension>, as shown in the following code.</span></span>

```csharp
DiscoveryOperationContextExtension doce = OperationContext.Current.Extensions.Find<DiscoveryOperationContextExtension>();
// Access the discovery version from the DiscoveryOperationContextExtension
doce.DiscoveryVersion;
```

## <a name="see-also"></a><span data-ttu-id="66727-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="66727-108">See also</span></span>

- <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion%2A>
- [<span data-ttu-id="66727-109">Implementace proxy zjišťování</span><span class="sxs-lookup"><span data-stu-id="66727-109">Implementing a Discovery Proxy</span></span>](implementing-a-discovery-proxy.md)
