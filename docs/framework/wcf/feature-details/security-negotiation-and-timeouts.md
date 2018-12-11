---
title: Vyjednávání a časové limity zabezpečení
ms.date: 03/30/2017
ms.assetid: 02a428f1-84e5-4d28-a11f-53ce31d63196
ms.openlocfilehash: dfabdb05c7658e3cf9eb5b325597360bbc0bb588
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53153398"
---
# <a name="security-negotiation-and-timeouts"></a><span data-ttu-id="9cf62-102">Vyjednávání a časové limity zabezpečení</span><span class="sxs-lookup"><span data-stu-id="9cf62-102">Security Negotiation and Timeouts</span></span>
<span data-ttu-id="9cf62-103">Při ověřování klientů a služeb, Windows Communication Foundation (WCF) podporuje režim, ve kterém se vyjedná přihlašovacích údajů služby ověřování v rámci.</span><span class="sxs-lookup"><span data-stu-id="9cf62-103">When clients and services authenticate, Windows Communication Foundation (WCF) supports a mode where the service credential is negotiated as part of authentication.</span></span> <span data-ttu-id="9cf62-104">V takových scénářích potenciálně více fáze exchange dochází mezi klientem a služba šíření přihlašovacích údajů služby ke klientovi.</span><span class="sxs-lookup"><span data-stu-id="9cf62-104">In such scenarios, a potentially multi-leg exchange occurs between the client and the service to propagate the service credential to the client.</span></span> <span data-ttu-id="9cf62-105"><xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> Vlastnost určuje, jak dlouho může trvat více fáze exchange k dokončení.</span><span class="sxs-lookup"><span data-stu-id="9cf62-105">The <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> property controls how long the multi-leg exchange can take to complete.</span></span> <span data-ttu-id="9cf62-106">Ale tento časový limit platí pouze v případě systému exchange ve skutečnosti má další, které jednu žádost odpověď.</span><span class="sxs-lookup"><span data-stu-id="9cf62-106">However, this timeout only applies if the exchange actually takes more that a single request-response.</span></span> <span data-ttu-id="9cf62-107">V případech, kde vyjednávání se dokončí v jediném odezvy časový limit se nevztahuje.</span><span class="sxs-lookup"><span data-stu-id="9cf62-107">In cases where the negotiation completes in a single round trip, the timeout does not apply.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cf62-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="9cf62-108">See Also</span></span>  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
 [<span data-ttu-id="9cf62-109">Jak: Sada Maxclockskew</span><span class="sxs-lookup"><span data-stu-id="9cf62-109">How to: Set a Max Clock Skew</span></span>](../../../../docs/framework/wcf/feature-details/how-to-set-a-max-clock-skew.md)
