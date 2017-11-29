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
# <a name="security-negotiation-and-timeouts"></a>Vyjednávání a časové limity zabezpečení
Při ověřování klientů a služeb, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] podporuje režim, kde se přihlašovací údaje služby vyjednávat jako součást ověřování. V takových scénářů potenciálně více větev exchange dojde mezi klientem a službu potřebný k šíření přihlašovací údaje služby do klienta. <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> Vlastnost určuje, jak dlouho může trvat víc větev exchange k dokončení. Však tento časový limit platí pouze v případě exchange ve skutečnosti trvá déle, jeden požadavků a odpovědí. V případech, kde vyjednávání dokončení v jediném odezvy nevztahuje časový limit.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
 [Postupy: Sada zkosení max. frekvence](../../../../docs/framework/wcf/feature-details/how-to-set-a-max-clock-skew.md)
