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
ms.openlocfilehash: b4d0b2953a91040c37afe88d9499fd4be1970f31
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="security-negotiation-and-timeouts"></a><span data-ttu-id="5c114-102">Vyjednávání a časové limity zabezpečení</span><span class="sxs-lookup"><span data-stu-id="5c114-102">Security Negotiation and Timeouts</span></span>
<span data-ttu-id="5c114-103">Při ověřování klientů a služeb, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] podporuje režim, kde se přihlašovací údaje služby vyjednávat jako součást ověřování.</span><span class="sxs-lookup"><span data-stu-id="5c114-103">When clients and services authenticate, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] supports a mode where the service credential is negotiated as part of authentication.</span></span> <span data-ttu-id="5c114-104">V takových scénářů potenciálně více větev exchange dojde mezi klientem a službu potřebný k šíření přihlašovací údaje služby do klienta.</span><span class="sxs-lookup"><span data-stu-id="5c114-104">In such scenarios, a potentially multi-leg exchange occurs between the client and the service to propagate the service credential to the client.</span></span> <span data-ttu-id="5c114-105"><xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> Vlastnost určuje, jak dlouho může trvat víc větev exchange k dokončení.</span><span class="sxs-lookup"><span data-stu-id="5c114-105">The <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> property controls how long the multi-leg exchange can take to complete.</span></span> <span data-ttu-id="5c114-106">Však tento časový limit platí pouze v případě exchange ve skutečnosti trvá déle, jeden požadavků a odpovědí.</span><span class="sxs-lookup"><span data-stu-id="5c114-106">However, this timeout only applies if the exchange actually takes more that a single request-response.</span></span> <span data-ttu-id="5c114-107">V případech, kde vyjednávání dokončení v jediném odezvy nevztahuje časový limit.</span><span class="sxs-lookup"><span data-stu-id="5c114-107">In cases where the negotiation completes in a single round trip, the timeout does not apply.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c114-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="5c114-108">See Also</span></span>  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
 [<span data-ttu-id="5c114-109">Postupy: Sada zkosení max. frekvence</span><span class="sxs-lookup"><span data-stu-id="5c114-109">How to: Set a Max Clock Skew</span></span>](../../../../docs/framework/wcf/feature-details/how-to-set-a-max-clock-skew.md)
