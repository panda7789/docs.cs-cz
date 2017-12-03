---
title: System.ServiceModel.Channels.PeerMaintainerActivity
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef28d086-d7fb-4e81-82e9-45a54647783b
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 71bcb16b89934f7f04cfd7d2f3c4b0ef3009dd78
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="systemservicemodelchannelspeermaintaineractivity"></a>System.ServiceModel.Channels.PeerMaintainerActivity
Modul PeerMaintainer provádí konkrétní operaci (podrobnosti obsažené v textu zprávy trasování).  
  
## <a name="description"></a>Popis  
 Trasování nastane během různé PeerMaintainer operace.  
  
 PeerMaintainer je interní součást Uzel PeerNode. Každou minutu nebo každých 32 zprávy přijaté, odešle zprávu LinkUtility pro své okolí s statistické údaje o tom, kolik zprávy se vyměňují a kolik jsou užitečné (bez duplikáty, untampered). To vám pomůže určit konkrétní sousedním odkaz nástroj. Přibližně každých pět minut, funkce maintainer kontroluje stav sousedním připojení. Pokud počet připojení sousedním překračuje ideální, funkce maintainer vyřazuje vypnout minimálně užitečné připojení. Pokud nejsou k dispozici dostatek připojení, funkce maintainer získá nové připojení.  
  
## <a name="see-also"></a>Viz také  
 [Trasování](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Řešení potíží s vaší aplikace pomocí trasování](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Správa a Diagnostika](../../../../../docs/framework/wcf/diagnostics/index.md)
