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
# <a name="security-negotiation-and-timeouts"></a>Vyjednávání a časové limity zabezpečení
Při ověřování klientů a služeb, Windows Communication Foundation (WCF) podporuje režim, ve kterém se vyjedná přihlašovacích údajů služby ověřování v rámci. V takových scénářích potenciálně více fáze exchange dochází mezi klientem a služba šíření přihlašovacích údajů služby ke klientovi. <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> Vlastnost určuje, jak dlouho může trvat více fáze exchange k dokončení. Ale tento časový limit platí pouze v případě systému exchange ve skutečnosti má další, které jednu žádost odpověď. V případech, kde vyjednávání se dokončí v jediném odezvy časový limit se nevztahuje.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
 [Jak: Sada Maxclockskew](../../../../docs/framework/wcf/feature-details/how-to-set-a-max-clock-skew.md)
