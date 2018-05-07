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
---
# <a name="security-negotiation-and-timeouts"></a>Vyjednávání a časové limity zabezpečení
Při ověřování klientů a služeb, Windows Communication Foundation (WCF) podporuje režim, kde se přihlašovací údaje služby vyjednávat jako součást ověřování. V takových scénářů potenciálně více větev exchange dojde mezi klientem a službu potřebný k šíření přihlašovací údaje služby do klienta. <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> Vlastnost určuje, jak dlouho může trvat víc větev exchange k dokončení. Však tento časový limit platí pouze v případě exchange ve skutečnosti trvá déle, jeden požadavků a odpovědí. V případech, kde vyjednávání dokončení v jediném odezvy nevztahuje časový limit.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
 [Postupy: Nastavení hodnoty vlastnosti MaxClockSkew](../../../../docs/framework/wcf/feature-details/how-to-set-a-max-clock-skew.md)
