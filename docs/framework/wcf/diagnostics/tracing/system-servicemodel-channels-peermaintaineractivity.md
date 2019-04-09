---
title: System.ServiceModel.Channels.PeerMaintainerActivity
ms.date: 03/30/2017
ms.assetid: ef28d086-d7fb-4e81-82e9-45a54647783b
ms.openlocfilehash: ea4c8110a8f820e0c6204fbd22b3d5b747709fba
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59126032"
---
# <a name="systemservicemodelchannelspeermaintaineractivity"></a>System.ServiceModel.Channels.PeerMaintainerActivity
Modul PeerMaintainer je provádění konkrétní operace (informace obsažené v textu zprávy trasování).  
  
## <a name="description"></a>Popis  
 Trasování nastane při různých operací PeerMaintainer.  
  
 PeerMaintainer je vnitřní komponenta PeerNode. Každou minutu nebo každých 32 zpráv přijme, odešle zpráva LinkUtility k jejím sousedům se statistikami o tom, kolik zprávy se vyměňují a kolik jsou užitečné (bez duplicitní, untampered). To vám pomůže určit konkrétní sousední propojení nástroje. Přibližně každých pět minut, funkce maintainer zkontroluje stav připojení sousedem. Pokud počet sousední připojení překročí ideální částka, funkce maintainer ořezává vypnout nejméně užitečné připojení. Pokud nejsou k dispozici dostatek připojení, funkce maintainer získává nové připojení.  
  
## <a name="see-also"></a>Viz také:

- [Trasování](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Řešení potíží s aplikací pomocí trasování](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Správa a diagnostika](../../../../../docs/framework/wcf/diagnostics/index.md)
