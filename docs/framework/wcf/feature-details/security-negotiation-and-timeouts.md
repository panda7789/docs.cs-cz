---
title: Vyjednávání a časové limity zabezpečení
ms.date: 03/30/2017
ms.assetid: 02a428f1-84e5-4d28-a11f-53ce31d63196
ms.openlocfilehash: a02c9d7b42eadf9a5ce9af8022fe292d6c23249c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59180638"
---
# <a name="security-negotiation-and-timeouts"></a>Vyjednávání a časové limity zabezpečení
Při ověřování klientů a služeb, Windows Communication Foundation (WCF) podporuje režim, ve kterém se vyjedná přihlašovacích údajů služby ověřování v rámci. V takových scénářích potenciálně více fáze exchange dochází mezi klientem a služba šíření přihlašovacích údajů služby ke klientovi. <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> Vlastnost určuje, jak dlouho může trvat více fáze exchange k dokončení. Ale tento časový limit platí pouze v případě systému exchange ve skutečnosti má další, které jednu žádost odpověď. V případech, kde vyjednávání se dokončí v jediném odezvy časový limit se nevztahuje.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- [Postupy: Nastvení hodnoty vlastnosti MaxClockSkew](../../../../docs/framework/wcf/feature-details/how-to-set-a-max-clock-skew.md)
