---
title: "Vyjednávání a časové limity zabezpečení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 02a428f1-84e5-4d28-a11f-53ce31d63196
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 6fbee18d31cb1774300c14587b0f7d973a4996ed
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="security-negotiation-and-timeouts"></a><span data-ttu-id="4681e-102">Vyjednávání a časové limity zabezpečení</span><span class="sxs-lookup"><span data-stu-id="4681e-102">Security Negotiation and Timeouts</span></span>
<span data-ttu-id="4681e-103">Při ověřování klientů a služeb, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] podporuje režim, kde se přihlašovací údaje služby vyjednávat jako součást ověřování.</span><span class="sxs-lookup"><span data-stu-id="4681e-103">When clients and services authenticate, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] supports a mode where the service credential is negotiated as part of authentication.</span></span> <span data-ttu-id="4681e-104">V takových scénářů potenciálně více větev exchange dojde mezi klientem a službu potřebný k šíření přihlašovací údaje služby do klienta.</span><span class="sxs-lookup"><span data-stu-id="4681e-104">In such scenarios, a potentially multi-leg exchange occurs between the client and the service to propagate the service credential to the client.</span></span> <span data-ttu-id="4681e-105"><xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> Vlastnost určuje, jak dlouho může trvat víc větev exchange k dokončení.</span><span class="sxs-lookup"><span data-stu-id="4681e-105">The <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> property controls how long the multi-leg exchange can take to complete.</span></span> <span data-ttu-id="4681e-106">Však tento časový limit platí pouze v případě exchange ve skutečnosti trvá déle, jeden požadavků a odpovědí.</span><span class="sxs-lookup"><span data-stu-id="4681e-106">However, this timeout only applies if the exchange actually takes more that a single request-response.</span></span> <span data-ttu-id="4681e-107">V případech, kde vyjednávání dokončení v jediném odezvy nevztahuje časový limit.</span><span class="sxs-lookup"><span data-stu-id="4681e-107">In cases where the negotiation completes in a single round trip, the timeout does not apply.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4681e-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="4681e-108">See Also</span></span>  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
 [<span data-ttu-id="4681e-109">Postupy: Nastavení hodnoty vlastnosti MaxClockSkew</span><span class="sxs-lookup"><span data-stu-id="4681e-109">How to: Set a Max Clock Skew</span></span>](../../../../docs/framework/wcf/feature-details/how-to-set-a-max-clock-skew.md)
