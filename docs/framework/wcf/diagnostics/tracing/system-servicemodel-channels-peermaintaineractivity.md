---
title: System.ServiceModel.Channels.PeerMaintainerActivity
ms.date: 03/30/2017
ms.assetid: ef28d086-d7fb-4e81-82e9-45a54647783b
ms.openlocfilehash: a7f353b00796c845f5686ca2926bbe7effe09e3e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33480581"
---
# <a name="systemservicemodelchannelspeermaintaineractivity"></a>System.ServiceModel.Channels.PeerMaintainerActivity
Modul PeerMaintainer provádí konkrétní operaci (podrobnosti obsažené v textu zprávy trasování).  
  
## <a name="description"></a>Popis  
 Trasování nastane během různé PeerMaintainer operace.  
  
 PeerMaintainer je interní součást Uzel PeerNode. Každou minutu nebo každých 32 zprávy přijaté, odešle zprávu LinkUtility pro své okolí s statistické údaje o tom, kolik zprávy se vyměňují a kolik jsou užitečné (bez duplikáty, untampered). To vám pomůže určit konkrétní sousedním odkaz nástroj. Přibližně každých pět minut, funkce maintainer kontroluje stav sousedním připojení. Pokud počet připojení sousedním překračuje ideální, funkce maintainer vyřazuje vypnout minimálně užitečné připojení. Pokud nejsou k dispozici dostatek připojení, funkce maintainer získá nové připojení.  
  
## <a name="see-also"></a>Viz také  
 [Trasování](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Řešení problémů s aplikací pomocí trasování](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Správa a diagnostika](../../../../../docs/framework/wcf/diagnostics/index.md)
