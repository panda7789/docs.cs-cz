---
title: PNRP při vývoji aplikací
ms.date: 03/30/2017
ms.assetid: 265615d6-4423-4b5d-8626-752e456f4f4e
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: b085604d7d20eb9222507b4820be219ffeae4726
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33395733"
---
# <a name="pnrp-in-application-development"></a><span data-ttu-id="60500-102">PNRP při vývoji aplikací</span><span class="sxs-lookup"><span data-stu-id="60500-102">PNRP in Application Development</span></span>
<span data-ttu-id="60500-103">V systému Windows Vista, síťové aplikace mohou přistupovat k název publikace a funkce řešení prostřednictvím zjednodušené PNRP aplikačního programovacího rozhraní (API).</span><span class="sxs-lookup"><span data-stu-id="60500-103">In Windows Vista, networking applications can access name publication and resolution functions through a simplified PNRP application programming interface (API).</span></span>  
  
## <a name="implementing-the-peer-name-resolution-protocol"></a><span data-ttu-id="60500-104">Implementace protokolu Peer Name Resolution Protocol</span><span class="sxs-lookup"><span data-stu-id="60500-104">Implementing the Peer Name Resolution Protocol</span></span>  
 <span data-ttu-id="60500-105">S zjednodušené rozhraní API PNRP nejsou explicitně zadané cloudy k registraci názvu a adresy; součást PNRP automaticky určuje příslušné cloud pro připojení a adresy publikovat v rámci cloudy.</span><span class="sxs-lookup"><span data-stu-id="60500-105">With the simplified PNRP API, clouds are not explicitly specified to register the name and addresses; the PNRP component automatically determines the appropriate clouds to join and the addresses to publish within the clouds.</span></span>  
  
 <span data-ttu-id="60500-106">Pro vysoce zjednodušené PNRP překlad IP adres v systému Windows Vista jsou integrovány do getaddrinfo() funkce Windows Sockets teď PNRP názvy.</span><span class="sxs-lookup"><span data-stu-id="60500-106">For highly simplified PNRP name resolution in Windows Vista, PNRP names are now integrated into the getaddrinfo() Windows Sockets function.</span></span> <span data-ttu-id="60500-107">Pokud chcete použít PNRP přeložit název na adresu IPv6, aplikace můžete použít funkci getaddrinfo() vyřešit name.prnp.net plně kvalifikovaný název domény (FQDN), který název je název partnerského zařízení přeloženy.</span><span class="sxs-lookup"><span data-stu-id="60500-107">To use PNRP to resolve a name to an IPv6 address, applications can use the getaddrinfo() function to resolve the Fully Qualified Domain Name (FQDN) name.prnp.net, in which name is peer name being resolved.</span></span> <span data-ttu-id="60500-108">Doména pnrp.net je vyhrazené domény v systému Windows Vista PNRP překladu IP adres.</span><span class="sxs-lookup"><span data-stu-id="60500-108">The pnrp.net domain is a reserved domain in Windows Vista for PNRP name resolution.</span></span>  
  
 <span data-ttu-id="60500-109">Předávání mezi aplikacemi PeerToPeer zpráv se stále provádí základní architektury, jako je například PeerChannel a WCF [velkého množství dat a Streaming](http://go.microsoft.com/fwlink/?LinkID=179652).</span><span class="sxs-lookup"><span data-stu-id="60500-109">Message passing between PeerToPeer applications is still handled by underlying architectures such as PeerChannel and WCF [Large Data and Streaming](http://go.microsoft.com/fwlink/?LinkID=179652).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60500-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="60500-110">See Also</span></span>  
 <xref:System.Net.PeerToPeer>
