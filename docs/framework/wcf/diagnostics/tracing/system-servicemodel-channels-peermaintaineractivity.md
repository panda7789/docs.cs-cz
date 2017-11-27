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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f3cde90bf5e9c57ff54378eaaf970aec219871a7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
