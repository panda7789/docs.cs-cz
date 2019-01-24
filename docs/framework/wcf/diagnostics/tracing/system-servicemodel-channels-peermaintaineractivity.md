---
title: System.ServiceModel.Channels.PeerMaintainerActivity
ms.date: 03/30/2017
ms.assetid: ef28d086-d7fb-4e81-82e9-45a54647783b
ms.openlocfilehash: 4c352ad4ac4ffee5d12c054590ef994bab0ba757
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54642578"
---
# <a name="systemservicemodelchannelspeermaintaineractivity"></a>System.ServiceModel.Channels.PeerMaintainerActivity
Modul PeerMaintainer je provádění konkrétní operace (informace obsažené v textu zprávy trasování).  
  
## <a name="description"></a>Popis  
 Trasování nastane při různých operací PeerMaintainer.  
  
 PeerMaintainer je vnitřní komponenta PeerNode. Každou minutu nebo každých 32 zpráv přijme, odešle zpráva LinkUtility k jejím sousedům se statistikami o tom, kolik zprávy se vyměňují a kolik jsou užitečné (bez duplicitní, untampered). To vám pomůže určit konkrétní sousední propojení nástroje. Přibližně každých pět minut, funkce maintainer zkontroluje stav připojení sousedem. Pokud počet sousední připojení překročí ideální částka, funkce maintainer ořezává vypnout nejméně užitečné připojení. Pokud nejsou k dispozici dostatek připojení, funkce maintainer získává nové připojení.  
  
## <a name="see-also"></a>Viz také:
- [Trasování](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Řešení problémů s aplikací pomocí trasování](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Správa a diagnostika](../../../../../docs/framework/wcf/diagnostics/index.md)
