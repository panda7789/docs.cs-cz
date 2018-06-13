---
title: Vyjednávání a časové limity zabezpečení
ms.date: 03/30/2017
ms.assetid: 02a428f1-84e5-4d28-a11f-53ce31d63196
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 508d648acf148f13076327bb312d0a0b08471ac1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33497461"
---
# <a name="security-negotiation-and-timeouts"></a><span data-ttu-id="eaceb-102">Vyjednávání a časové limity zabezpečení</span><span class="sxs-lookup"><span data-stu-id="eaceb-102">Security Negotiation and Timeouts</span></span>
<span data-ttu-id="eaceb-103">Při ověřování klientů a služeb, Windows Communication Foundation (WCF) podporuje režim, kde se přihlašovací údaje služby vyjednávat jako součást ověřování.</span><span class="sxs-lookup"><span data-stu-id="eaceb-103">When clients and services authenticate, Windows Communication Foundation (WCF) supports a mode where the service credential is negotiated as part of authentication.</span></span> <span data-ttu-id="eaceb-104">V takových scénářů potenciálně více větev exchange dojde mezi klientem a službu potřebný k šíření přihlašovací údaje služby do klienta.</span><span class="sxs-lookup"><span data-stu-id="eaceb-104">In such scenarios, a potentially multi-leg exchange occurs between the client and the service to propagate the service credential to the client.</span></span> <span data-ttu-id="eaceb-105"><xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> Vlastnost určuje, jak dlouho může trvat víc větev exchange k dokončení.</span><span class="sxs-lookup"><span data-stu-id="eaceb-105">The <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> property controls how long the multi-leg exchange can take to complete.</span></span> <span data-ttu-id="eaceb-106">Však tento časový limit platí pouze v případě exchange ve skutečnosti trvá déle, jeden požadavků a odpovědí.</span><span class="sxs-lookup"><span data-stu-id="eaceb-106">However, this timeout only applies if the exchange actually takes more that a single request-response.</span></span> <span data-ttu-id="eaceb-107">V případech, kde vyjednávání dokončení v jediném odezvy nevztahuje časový limit.</span><span class="sxs-lookup"><span data-stu-id="eaceb-107">In cases where the negotiation completes in a single round trip, the timeout does not apply.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eaceb-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="eaceb-108">See Also</span></span>  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
 [<span data-ttu-id="eaceb-109">Postupy: Nastavení hodnoty vlastnosti MaxClockSkew</span><span class="sxs-lookup"><span data-stu-id="eaceb-109">How to: Set a Max Clock Skew</span></span>](../../../../docs/framework/wcf/feature-details/how-to-set-a-max-clock-skew.md)
