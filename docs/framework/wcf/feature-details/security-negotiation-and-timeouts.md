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
# <a name="security-negotiation-and-timeouts"></a>Vyjednávání a časové limity zabezpečení
Při ověřování klientů a služeb, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] podporuje režim, kde se přihlašovací údaje služby vyjednávat jako součást ověřování. V takových scénářů potenciálně více větev exchange dojde mezi klientem a službu potřebný k šíření přihlašovací údaje služby do klienta. <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> Vlastnost určuje, jak dlouho může trvat víc větev exchange k dokončení. Však tento časový limit platí pouze v případě exchange ve skutečnosti trvá déle, jeden požadavků a odpovědí. V případech, kde vyjednávání dokončení v jediném odezvy nevztahuje časový limit.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
 [Postupy: Nastavení hodnoty vlastnosti MaxClockSkew](../../../../docs/framework/wcf/feature-details/how-to-set-a-max-clock-skew.md)
