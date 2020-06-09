---
title: System.ServiceModel.Channels.PeerMaintainerActivity
ms.date: 03/30/2017
ms.assetid: ef28d086-d7fb-4e81-82e9-45a54647783b
ms.openlocfilehash: ce97eaa2ad5c9dbd5f4d6f81186960c489eb4b85
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596074"
---
# <a name="systemservicemodelchannelspeermaintaineractivity"></a>System.ServiceModel.Channels.PeerMaintainerActivity
Modul činnost PeerMaintainer provádí konkrétní operaci (podrobnosti najdete v těle trasovací zprávy).  
  
## <a name="description"></a>Popis  
 K tomuto trasování dochází během různých činnost PeerMaintainer operací.  
  
 Činnost PeerMaintainer je interní komponenta PeerNode. Každou minutu nebo všechny přijaté zprávy 32 pošle zprávu LinkUtility svým sousedům se statistikou o počtu vyměňovaných zpráv a počtu užitečných (neoprávněných duplicit). To pomáhá určit určitý sousední Nástroj pro propojení. Přibližně každých pět minut udržuje údržba stav sousedních připojení. Pokud počet sousedních připojení překročí ideální množství, vyřadí ho údržba nejméně užitečná připojení. Pokud není k dispozici dostatek připojení, údržba získá nová připojení.  
  
## <a name="see-also"></a>Viz také

- [Trasování](index.md)
- [Řešení potíží s aplikací pomocí trasování](using-tracing-to-troubleshoot-your-application.md)
- [Správa a diagnostika](../index.md)
