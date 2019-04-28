---
title: System.ServiceModel.Channels.FailedAcceptFromPool
ms.date: 03/30/2017
ms.assetid: d535b1b5-ee58-45e8-b400-7d9570f4eb9a
ms.openlocfilehash: de0bdd9e5ab922b09249bf550fde745042be8e58
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61666752"
---
# <a name="systemservicemodelchannelsfailedacceptfrompool"></a>System.ServiceModel.Channels.FailedAcceptFromPool
Pokus o opakované použití připojení ve fondu se nezdařil. Další pokus se uskuteční v rámci určeného časového limitu.  
  
## <a name="description"></a>Popis  
 Tento informační trasování označuje, že došlo k chybě při pokusu o opakované použití ve fondu připojení. Může k tomu dojít, protože ve fondu připojení není kompatibilní, připravené nebo stále aktivní. Další pokusy o opakované použití dalších klientů ve fondu připojení jsou provedeny v daném časovém limitu a v případě, že se nenašla žádná použitelná připojení, vytvoří se nové připojení.  
  
## <a name="see-also"></a>Viz také:

- [Trasování](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Řešení problémů s aplikací pomocí trasování](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Správa a diagnostika](../../../../../docs/framework/wcf/diagnostics/index.md)
