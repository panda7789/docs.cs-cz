---
title: Vyjednávání a časové limity zabezpečení
ms.date: 03/30/2017
ms.assetid: 02a428f1-84e5-4d28-a11f-53ce31d63196
ms.openlocfilehash: a02c9d7b42eadf9a5ce9af8022fe292d6c23249c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59180638"
---
# <a name="security-negotiation-and-timeouts"></a><span data-ttu-id="8b6c8-102">Vyjednávání a časové limity zabezpečení</span><span class="sxs-lookup"><span data-stu-id="8b6c8-102">Security Negotiation and Timeouts</span></span>
<span data-ttu-id="8b6c8-103">Při ověřování klientů a služeb, Windows Communication Foundation (WCF) podporuje režim, ve kterém se vyjedná přihlašovacích údajů služby ověřování v rámci.</span><span class="sxs-lookup"><span data-stu-id="8b6c8-103">When clients and services authenticate, Windows Communication Foundation (WCF) supports a mode where the service credential is negotiated as part of authentication.</span></span> <span data-ttu-id="8b6c8-104">V takových scénářích potenciálně více fáze exchange dochází mezi klientem a služba šíření přihlašovacích údajů služby ke klientovi.</span><span class="sxs-lookup"><span data-stu-id="8b6c8-104">In such scenarios, a potentially multi-leg exchange occurs between the client and the service to propagate the service credential to the client.</span></span> <span data-ttu-id="8b6c8-105"><xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> Vlastnost určuje, jak dlouho může trvat více fáze exchange k dokončení.</span><span class="sxs-lookup"><span data-stu-id="8b6c8-105">The <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> property controls how long the multi-leg exchange can take to complete.</span></span> <span data-ttu-id="8b6c8-106">Ale tento časový limit platí pouze v případě systému exchange ve skutečnosti má další, které jednu žádost odpověď.</span><span class="sxs-lookup"><span data-stu-id="8b6c8-106">However, this timeout only applies if the exchange actually takes more that a single request-response.</span></span> <span data-ttu-id="8b6c8-107">V případech, kde vyjednávání se dokončí v jediném odezvy časový limit se nevztahuje.</span><span class="sxs-lookup"><span data-stu-id="8b6c8-107">In cases where the negotiation completes in a single round trip, the timeout does not apply.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b6c8-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8b6c8-108">See also</span></span>

- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- [<span data-ttu-id="8b6c8-109">Postupy: Sada Maxclockskew</span><span class="sxs-lookup"><span data-stu-id="8b6c8-109">How to: Set a Max Clock Skew</span></span>](../../../../docs/framework/wcf/feature-details/how-to-set-a-max-clock-skew.md)
