---
title: Vyjednávání a časové limity zabezpečení
ms.date: 03/30/2017
ms.assetid: 02a428f1-84e5-4d28-a11f-53ce31d63196
ms.openlocfilehash: 1b5fb15b4ea00ba33b741c96bcb423aefe9890fa
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600994"
---
# <a name="security-negotiation-and-timeouts"></a><span data-ttu-id="17987-102">Vyjednávání a časové limity zabezpečení</span><span class="sxs-lookup"><span data-stu-id="17987-102">Security Negotiation and Timeouts</span></span>
<span data-ttu-id="17987-103">Když klienti a služby ověřují, Windows Communication Foundation (WCF) podporuje režim, ve kterém je pověření služby vyjednáno jako součást ověřování.</span><span class="sxs-lookup"><span data-stu-id="17987-103">When clients and services authenticate, Windows Communication Foundation (WCF) supports a mode where the service credential is negotiated as part of authentication.</span></span> <span data-ttu-id="17987-104">V takových scénářích dojde k nenáročnému Exchangi mezi klientem a službou, aby bylo možné rozšířit pověření služby na klienta.</span><span class="sxs-lookup"><span data-stu-id="17987-104">In such scenarios, a potentially multi-leg exchange occurs between the client and the service to propagate the service credential to the client.</span></span> <span data-ttu-id="17987-105"><xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A>Vlastnost určuje dobu, po kterou může trvat vícenásobné výměny ramen.</span><span class="sxs-lookup"><span data-stu-id="17987-105">The <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> property controls how long the multi-leg exchange can take to complete.</span></span> <span data-ttu-id="17987-106">Tento časový limit se však vztahuje pouze v případě, že výměna ve skutečnosti trvá více, než jedna odpověď na požadavek.</span><span class="sxs-lookup"><span data-stu-id="17987-106">However, this timeout only applies if the exchange actually takes more that a single request-response.</span></span> <span data-ttu-id="17987-107">V případech, kdy se vyjednávání dokončí v jedné operaci odezvy, se nepoužije časový limit.</span><span class="sxs-lookup"><span data-stu-id="17987-107">In cases where the negotiation completes in a single round trip, the timeout does not apply.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17987-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="17987-108">See also</span></span>

- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- [<span data-ttu-id="17987-109">Postupy: Nastavení hodnoty vlastnosti MaxClockSkew</span><span class="sxs-lookup"><span data-stu-id="17987-109">How to: Set a Max Clock Skew</span></span>](how-to-set-a-max-clock-skew.md)
