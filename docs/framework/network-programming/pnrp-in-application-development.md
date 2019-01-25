---
title: PNRP ve vývoji aplikací
ms.date: 03/30/2017
ms.assetid: 265615d6-4423-4b5d-8626-752e456f4f4e
ms.openlocfilehash: 93dd65100e19f16c6597374cbab1e10d6a759562
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54736543"
---
# <a name="pnrp-in-application-development"></a><span data-ttu-id="ec4c9-102">PNRP ve vývoji aplikací</span><span class="sxs-lookup"><span data-stu-id="ec4c9-102">PNRP in Application Development</span></span>
<span data-ttu-id="ec4c9-103">Ve Windows Vista, síťové aplikace můžou k název publikace a funkce řešení prostřednictvím zjednodušené PNRP aplikačního programovacího rozhraní (API).</span><span class="sxs-lookup"><span data-stu-id="ec4c9-103">In Windows Vista, networking applications can access name publication and resolution functions through a simplified PNRP application programming interface (API).</span></span>  
  
## <a name="implementing-the-peer-name-resolution-protocol"></a><span data-ttu-id="ec4c9-104">Implementace protokolu Peer Name Resolution Protocol</span><span class="sxs-lookup"><span data-stu-id="ec4c9-104">Implementing the Peer Name Resolution Protocol</span></span>  
 <span data-ttu-id="ec4c9-105">Zjednodušené rozhraní API PNRP nejsou explicitně zadané cloudy registrace názvu a adresy; komponenta PNRP automaticky určuje odpovídající cloudy spojení a adresy, které mají publikovat v rámci cloudy.</span><span class="sxs-lookup"><span data-stu-id="ec4c9-105">With the simplified PNRP API, clouds are not explicitly specified to register the name and addresses; the PNRP component automatically determines the appropriate clouds to join and the addresses to publish within the clouds.</span></span>  
  
 <span data-ttu-id="ec4c9-106">Pro velmi zjednodušené PNRP překlad ve Windows Vista PNRP názvy jsou teď integrovaná v getaddrinfo() – funkce rozhraní Windows Sockets.</span><span class="sxs-lookup"><span data-stu-id="ec4c9-106">For highly simplified PNRP name resolution in Windows Vista, PNRP names are now integrated into the getaddrinfo() Windows Sockets function.</span></span> <span data-ttu-id="ec4c9-107">Pomocí protokolu PNRP přeložit název na adresu IPv6, aplikace můžou využít funkci getaddrinfo() vyřešit name.prnp.net plně kvalifikovaný název domény (FQDN), který název je název partnerského zařízení probíhá řešení.</span><span class="sxs-lookup"><span data-stu-id="ec4c9-107">To use PNRP to resolve a name to an IPv6 address, applications can use the getaddrinfo() function to resolve the Fully Qualified Domain Name (FQDN) name.prnp.net, in which name is peer name being resolved.</span></span> <span data-ttu-id="ec4c9-108">Doména pnrp.net je vyhrazené domény ve Windows Vista k rozlišení názvu PNRP.</span><span class="sxs-lookup"><span data-stu-id="ec4c9-108">The pnrp.net domain is a reserved domain in Windows Vista for PNRP name resolution.</span></span>  
  
 <span data-ttu-id="ec4c9-109">Předávání mezi aplikacemi PeerToPeer zpráv stále zpracovává základní architektury, jako je například kanál PeerChannel a WCF [velkých objemů dat a datových proudů](https://go.microsoft.com/fwlink/?LinkID=179652).</span><span class="sxs-lookup"><span data-stu-id="ec4c9-109">Message passing between PeerToPeer applications is still handled by underlying architectures such as PeerChannel and WCF [Large Data and Streaming](https://go.microsoft.com/fwlink/?LinkID=179652).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec4c9-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ec4c9-110">See also</span></span>
- <xref:System.Net.PeerToPeer>
