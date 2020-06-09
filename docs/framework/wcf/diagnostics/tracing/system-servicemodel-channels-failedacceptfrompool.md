---
title: System.ServiceModel.Channels.FailedAcceptFromPool
ms.date: 03/30/2017
ms.assetid: d535b1b5-ee58-45e8-b400-7d9570f4eb9a
ms.openlocfilehash: 5bfa31d0eaf3b00017512eddc60bfa99eda619e3
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84582579"
---
# <a name="systemservicemodelchannelsfailedacceptfrompool"></a>System.ServiceModel.Channels.FailedAcceptFromPool
Pokus o opakované použití sdruženého připojení se nezdařil. V zadaném časovém limitu se provede další pokus.  
  
## <a name="description"></a>Popis  
 Toto informační trasování indikuje, že došlo k chybě při pokusu o opakované použití připojení ve fondu. K tomu může dojít, protože připojení ve fondu není kompatibilní, připravené nebo pořád aktivní. Další pokusy o opakované použití jiných sdružených připojení se provedou v daném časovém limitu a vytvoří se nové připojení pro případ, že se nenaleznou žádná použitelná připojení.  
  
## <a name="see-also"></a>Viz také

- [Trasování](index.md)
- [Řešení potíží s aplikací pomocí trasování](using-tracing-to-troubleshoot-your-application.md)
- [Správa a diagnostika](../index.md)
