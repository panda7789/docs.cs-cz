---
title: PNRP ve vývoji aplikací
ms.date: 03/30/2017
ms.assetid: 265615d6-4423-4b5d-8626-752e456f4f4e
ms.openlocfilehash: f9a408fbd7fbbb77c0fd5208926f4b06fcf23b38
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74428203"
---
# <a name="pnrp-in-application-development"></a><span data-ttu-id="81010-102">PNRP ve vývoji aplikací</span><span class="sxs-lookup"><span data-stu-id="81010-102">PNRP in Application Development</span></span>
<span data-ttu-id="81010-103">V systému Windows Vista mohou síťové aplikace přistupovat k funkcím publikování názvů a rozlišení prostřednictvím zjednodušeného aplikačního programovacího rozhraní (API) protokolu PNRP.</span><span class="sxs-lookup"><span data-stu-id="81010-103">In Windows Vista, networking applications can access name publication and resolution functions through a simplified PNRP application programming interface (API).</span></span>  
  
## <a name="implementing-the-peer-name-resolution-protocol"></a><span data-ttu-id="81010-104">Implementace protokolu pro překlad názvů rovnocenných stran</span><span class="sxs-lookup"><span data-stu-id="81010-104">Implementing the Peer Name Resolution Protocol</span></span>  
 <span data-ttu-id="81010-105">Pomocí zjednodušeného rozhraní PNRP API nejsou mraky explicitně určeny pro registraci názvu a adres. Komponenta PNRP automaticky určuje příslušné cloudy, které se mají spojit, a adresy, které mají být publikovány v rámci cloudů.</span><span class="sxs-lookup"><span data-stu-id="81010-105">With the simplified PNRP API, clouds are not explicitly specified to register the name and addresses; the PNRP component automatically determines the appropriate clouds to join and the addresses to publish within the clouds.</span></span>  
  
 <span data-ttu-id="81010-106">Pro velmi zjednodušené překlad názvů PNRP v systému Windows Vista, PNRP názvy jsou nyní integrovány do getaddrinfo() Windows Sockets funkce.</span><span class="sxs-lookup"><span data-stu-id="81010-106">For highly simplified PNRP name resolution in Windows Vista, PNRP names are now integrated into the getaddrinfo() Windows Sockets function.</span></span> <span data-ttu-id="81010-107">Chcete-li použít PNRP k překladu názvu na adresu IPv6, mohou aplikace použít funkci getaddrinfo() k vyřešení plně kvalifikovaného názvu domény (FQDN) name.prnp.net, ve kterém je název peer název přeložen.</span><span class="sxs-lookup"><span data-stu-id="81010-107">To use PNRP to resolve a name to an IPv6 address, applications can use the getaddrinfo() function to resolve the Fully Qualified Domain Name (FQDN) name.prnp.net, in which name is peer name being resolved.</span></span> <span data-ttu-id="81010-108">Doména pnrp.net je vyhrazená doména v systému Windows Vista pro překlad názvů PNRP.</span><span class="sxs-lookup"><span data-stu-id="81010-108">The pnrp.net domain is a reserved domain in Windows Vista for PNRP name resolution.</span></span>  
  
 <span data-ttu-id="81010-109">Zprávy předávají mezi aplikacemi PeerToPeer je stále zpracovává základní architektury, jako je PeerChannel a WCF [velkých dat a streamování](../wcf/feature-details/large-data-and-streaming.md).</span><span class="sxs-lookup"><span data-stu-id="81010-109">Message passing between PeerToPeer applications is still handled by underlying architectures such as PeerChannel and WCF [Large Data and Streaming](../wcf/feature-details/large-data-and-streaming.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81010-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="81010-110">See also</span></span>

- <xref:System.Net.PeerToPeer>
